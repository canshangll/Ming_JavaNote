# JavaEE 项目的三层架构

![JavaEE三层架构](E:\java\javaweb\笔记\images\三层架构\JavaEE三层架构.png)

```java
分层的目的是为了解耦。解耦就是为了降低代码的耦合度。方便项目后期的维护和升级。
```

```java
web 层 com.lmj.web/servlet/controller 
    
service 层 com.lmj.service Service 接口包 
    	   com.lmj.service.impl Service 接口实现类 
    
dao 持久层 com.lmj.dao Dao 接口包 
    	  com.lmj.dao.impl Dao 接口实现类 
    
实体 bean 对象 com.lmj.pojo/entity/domain/bean JavaBean 类 
    
测试包 com.lmj.test/junit 
    
工具类 com.lmj.utils
```

![三层架构](E:\java\javaweb\笔记\images\三层架构\三层架构.png)

### 1、数据库和表

```sql
drop database if exists book; 
create database book; 
use book; 
create table t_user( 
    `id` int primary key auto_increment, 
    `username` varchar(20) not null unique, 
    `password` varchar(32) not null, 
    `email` varchar(200) 
);
insert into t_user(`username`,`password`,`email`) values('admin','admin','admin@atguigu.com'); 
select * from t_user;
```

### 2、数据库表对应的JavaBean对象

```java
public class User {
    private Integer id;
    private String username;
    private String password;
    private String email;
    ...
}
```

### 3、编写工具类JdbcUtils

#### 3.1导入jar包(数据库和连接池需要)

 [druid-1.1.9.jar](资料\JavaWeb需要用到的jar包\druid-1.1.9.jar) 

 [mysql-connector-java-5.1.7-bin.jar](资料\JavaWeb需要用到的jar包\mysql-connector-java-5.1.7-bin.jar) 

#### 3.2在src源码目录下编写配置文件

jdbc.properties

```properties
username=root 
password=root 
url=jdbc:mysql://localhost:3306/book 
driverClassName=com.mysql.jdbc.Driver 
initialSize=5 
maxActive=10
```

#### 3.3编写JdbcUtils工具类

```java
public class JdbcUtils {
    private static DruidDataSource dataSource;
    static {
        try {
            Properties properties = new Properties();
            //读取 jdbc.properties属性配置文件
            InputStream inputStream = com.alibaba.druid.util.JdbcUtils.class.getClassLoader().getResourceAsStream("jdbc.properties");
            //从流中加载数据
            properties.load(inputStream);
            //创建数据库的连接池
            dataSource = (DruidDataSource) DruidDataSourceFactory.createDataSource(properties);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
    /**
     * 连接数据库连接池中的连接
     *
     * @return
     */
    public static Connection getConnection() {
        Connection conn = null;
        try {
            conn = dataSource.getConnection();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return conn;
    }

    /**
     * 关闭连接，放回数据库连接池
     *
     * @param conn
     */
    public static void close(Connection conn) {
        if (conn != null){
            try {
                conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```

#### 3.4JdbcUtils测试

```java
public class JdbcUtilsTest {
    @Test
    public void testJdbcUtils() {
        for (int i = 0; i < 100; i++) {
            Connection connection = JdbcUtils.getConnection();
            System.out.println(connection);
            JdbcUtils.close(connection);
        }
    }
}
```

### 4、编写BaseDao

#### 4.1导入DBUtils的jar包

 [commons-dbutils-1.3.jar](资料\JavaWeb需要用到的jar包\commons-dbutils-1.3.jar) 

#### 4.2编写BaseBao

```java
public abstract class BaseDao {
    //使用DbUtils 操作数据库
    private QueryRunner queryRunner = new QueryRunner();
    /**
     * update()方法用来执行 增删改语句
     *
     * @return 如果返回-1，说明执行失败<br/>返回其他表示影响的行数
     */
    public int update(String sql, Object... args) {
        Connection connection = JdbcUtils.getConnection();
        try {
            return queryRunner.update(connection, sql, args);
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            JdbcUtils.close(connection);
        }
        return -1;
    }
    /**
     * 查询返回一个JavaBean的sql语句
     *
     * @param type 返回的对象类型
     * @param sql  执行的sql语句
     * @param args sql对应的参数值
     * @param <T>  返回的类型的泛型
     * @return
     */
    public <T> T queryForOne(Class<T> type, String sql, Object... args) {
        Connection conn = JdbcUtils.getConnection();
        try {
            return queryRunner.query(conn, sql, new BeanHandler<T>(type), args);
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            JdbcUtils.close(conn);
        }
        return null;
    }
    /**
     * 查询返回多个JavaBean的sql语句
     *
     * @param type 返回的对象类型
     * @param sql  执行的sql语句
     * @param args sql对应的参数值
     * @param <T>  返回的类型的泛型
     * @return
     */
    public <T> List<T> queryForList(Class<T> type, String sql, Object... args) {
        Connection conn = JdbcUtils.getConnection();
        try {
            return queryRunner.query(conn, sql, new BeanListHandler<T>(type), args);
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            JdbcUtils.close(conn);
        }
        return null;
    }
    /**
     * 执行返回一行一列的sql语句
     * @param sql   执行的sql语句
     * @param args  sql对应的参数值
     * @return
     */
    public Object queryForSingleValue(String sql, Object... args) {
        Connection conn = JdbcUtils.getConnection();
        try {
            return queryRunner.query(conn, sql, new ScalarHandler(), args);
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            JdbcUtils.close(conn);
        }
        return null;
    }
}
```

### 5、编写UserDao

#### 5.1UserDao接口：

```java
public interface UserDao {
    /**
     * 根据用户名查询用户信息
     * @param username  用户名
     * @return  如果返回null,说明没有这个用户。返之亦然
     */
    public User queryUserByUsername(String username);
    /**
     * 根据 用户名和密码查询用户信息
     * @param username
     * @param password
     * @return 如果返回null，说明用户名或密码错误，反之亦然
     */
    public User queryUserByUsernameAndPassword(String username,String password);
    /**
     * 保存用户信息
     * @param user
     * @return 返回-1表示操作失败，其他是sql语句影响的行数
     */
    public int saveUser(User user);
}
```

#### 5.2UserDaoImpl实现类

```java
public class UserDaoImpl extends BaseDao implements UserDao {
    @Override
    public User queryUserByUsername(String username) {
        String sql = "select `id`,`username`,`password`,`email` from t_user where username = ?";
        return queryForOne(User.class, sql, username);
    }
    @Override
    public User queryUserByUsernameAndPassword(String username, String password) {
        String sql = "select `id`,`username`,`password`,`email` from t_user where username = ? and password = ?";
        return queryForOne(User.class, sql, username, password);
    }
    @Override
    public int saveUser(User user) {
        String sql = "insert into t_user(`username`,`password`,`email`) values(?,?,?)";
        return  update(sql,user.getUsername(),user.getPassword(),user.getEmail());
    }
}
```

#### UserDao测试

```java
public class UserDaoTest {
    UserDao userDao = new UserDaoImpl();
    @Test
    public void queryUserByUsername() {
        if (userDao.queryUserByUsername("admin234") == null) {
            System.out.println("用户名可用！");
        } else {
            System.out.println("用户名已存在！");
        }
    }
    @Test
    public void queryUserByUsernameAndPassword() {
        if (userDao.queryUserByUsernameAndPassword("admin", "admin") == null) {
            System.out.println("用户名或密码错误，登录失败");
        }else {
            System.out.println("登录成功");
        }
    }
    @Test
    public void saveUser() {
        System.out.println(userDao.saveUser(new User(null,"admin13","123456","lmj@qq.com")));
    }
}
```

### 6、编写UserService

#### 6.1UserService接口

```java
public interface UserService {
    /**
     * 注册用户
     * @param user
     */
    public void registUser(User user);
    /**
     * 登录
     * @param user
     * @return 如果返回null，说明登录失败，其他：登录成功
     */
    public User login(User user);
    /**
     * 检查 用户名是否可用
     * @param username
     * @return 返回true表示用户名已存在，返回false表示用户名可用
     */
    public boolean existsUsername(String username);
}
```

#### UserServiceImpl实现类

```java
public class UserServiceImpl implements UserService {
    private UserDao userDao = new UserDaoImpl();
    @Override
    public void registUser(User user) {
        userDao.saveUser(user);
    }
    @Override
    public User login(User user) {
        return userDao.queryUserByUsernameAndPassword(user.getUsername(), user.getPassword());
    }
    @Override
    public boolean existsUsername(String username) {
        if (userDao.queryUserByUsername(username) == null){
            //等于null，说明没查到，没查到表示可用
            return false;
        }
        return true;
    }
}
```

#### UserService测试

```java
public class UserServiceTest {
    UserService userService = new UserServiceImpl();
    @Test
    public void registUser() {
        userService.registUser(new User(null, "lmjmm", "123456", "123@123.com"));
        userService.registUser(new User(null, "lmjgg", "123456", "12345@123.com"));
    }
    @Test
    public void login() {
        System.out.println(userService.login(new User(null, "lmjmm", "123456", null)));
    }
    @Test
    public void existsUsername() {
        if (userService.existsUsername("lmjmm")){
            System.out.println("用户名已存在！");
        }else {
            System.out.println("用户名可用！");
        }
    }
}
```

### 7、编写web层

#### 7.1实现用户注册的功能

RegistServlet.java

```java
public class RegistServlet extends HttpServlet {
    private UserService userService = new UserServiceImpl();
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求的参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String email = req.getParameter("email");
        String code = req.getParameter("code");
        //验证码验证
        if ("abcde".equalsIgnoreCase(code)) {
            //检查用户名是否可用
            if (userService.existsUsername(username)) {
                System.out.println("用户名[" + username + "]已存在！");
                //跳回注册页面
req.getRequestDispatcher("/pages/user/regist.html").forward(req, resp);
            } else {
                //调用Service保存到数据库
                userService.registUser(new User(null, username, password, email));
                //跳到注册成功页面 regist_success.html
req.getRequestDispatcher("/pages/user/regist_success.html").forward(req, resp);
            }
        } else {
            System.out.println("验证码[" + code + "]错误");
req.getRequestDispatcher("/pages/user/regist.html").forward(req, resp);
        }
    }
}
```

#### 7.2实现用户登录功能

```java
public class LoginServlet extends HttpServlet {
    private UserService userService = new UserServiceImpl();
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求的参数
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        //调用userService.Login()登录处理业务
        User loginUser = userService.login(new User(null, username, password, null));
        //如果等于null,说明登录失败！
        if (loginUser == null) {
            System.out.println("用户名或密码错误，登录失败！");
req.getRequestDispatcher("/pages/user/login.html").forward(req, resp);
        } else {
            //登录成功
req.getRequestDispatcher("/pages/user/login_success.html").forward(req, resp);
        }
    }
}
```




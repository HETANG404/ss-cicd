Spring Boot 项目的通用结构是高度模块化、清晰分层的。下面是一个典型的 Spring Boot 项目目录结构（遵循最佳实践）：

```
my-springboot-app/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── example/
│       │           └── myapp/
│       │               ├── MyAppApplication.java        # 启动类（@SpringBootApplication）
│       │               │
│       │               ├── controller/                  # 控制器层（Web 接口）
│       │               │   └── UserController.java
│       │               │
│       │               ├── service/                     # 业务逻辑层
│       │               │   └── UserService.java
│       │               │
│       │               ├── service/impl/                # 业务逻辑实现
│       │               │   └── UserServiceImpl.java
│       │               │
│       │               ├── repository/                  # 数据访问层（DAO）
│       │               │   └── UserRepository.java
│       │               │
│       │               ├── model/                       # 实体类（通常对应数据库表）
│       │               │   └── User.java
│       │               │
│       │               ├── dto/                         # 数据传输对象
│       │               │   └── UserDTO.java
│       │               │
│       │               ├── config/                      # 配置类（如 CORS、安全等）
│       │               │   └── WebConfig.java
│       │               │
│       │               └── exception/                   # 全局异常处理
│       │                   └── GlobalExceptionHandler.java
│       │
│       └── resources/
│           ├── application.yml                          # Spring Boot 配置文件
│           ├── static/                                  # 静态资源（如 HTML、CSS、JS）
│           ├── templates/                               # 模板文件（如 Thymeleaf）
│           └── messages.properties                      # 国际化资源
│
├── pom.xml                                               # Maven 构建文件
└── README.md                                             # 项目说明文档
```

---

### 各模块职责说明：

| 模块           | 职责简述                         |
| ------------ | ---------------------------- |
| `controller` | 接收 HTTP 请求，返回响应（REST API 层）  |
| `service`    | 编写核心业务逻辑，处理数据交互              |
| `repository` | 与数据库交互（通常使用 Spring Data JPA） |
| `model`      | 实体类，对应数据库表结构                 |
| `dto`        | 用于数据传输，避免暴露实体细节              |
| `config`     | 存放各种配置，如跨域、安全、Swagger 等      |
| `exception`  | 全局异常处理，提升程序健壮性               |
| `resources`  | 项目的非 Java 文件资源，如配置、静态资源等     |



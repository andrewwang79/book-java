# 单元测试
## 资料
* [Mockito demo](https://www.springboottutorial.com/spring-boot-unit-testing-and-mocking-with-mockito-and-junit)
* [Testing in Spring Boot 2](https://howtodoinjava.com/spring-boot2/testing/testing-support/)
* [使用强大的 Mockito 来测试你的代码](https://cloud.tencent.com/developer/article/1056721)
* https://juejin.im/post/6844903924248346637
* [Eclipse使用EclEmma看单元测试的代码覆盖率](https://www.cnblogs.com/wuxun1997/p/8480056.html)

## 规则
1. 用例分类: 基础类，Service，Controller
1. 数据放在test目录下
1. 持久化有CUD的，需用try-finally清理。比如数据库
1. MOCK用途：本质是替换函数
  1. 无法管理的：操作系统服务(获取MAC)，外部服务(OSS服务)
  1. 不方便的：数据库

## 单元测试代码编写
* [编写参考](https://juejin.cn/post/6844903924248346637)
* [exception](https://www.baeldung.com/junit-assert-exception)

```java
@Service
public class ProjectService {
    @Autowired
    private ProjectMapper mapper;

    public ProjectDO detail(String id) {
        return mapper.selectById(id);
    }
}

@RunWith(SpringRunner.class)
@SpringBootTest
public class ProjectServiceTest {
    @MockBean
    private ProjectMapper mapper;
    @Autowired
    private ProjectService service;

    @Test
    public void detail() {
        ProjectDemoDO model = new ProjectDemoDO("1", "demo");
        Mockito.when(mapper.selectById("1")).thenReturn(model);
        ProjectDemoDO entity = service.detail("1");
        assertThat(entity.getName(), containsString("demo"));
    }
}
```

```java
@RestController
@RequestMapping("v1/users")
public class UserController {
    @GetMapping("/{id}")
    public User get(@PathVariable("id") String id) {
        return new User(1, "lyTongXue");
    }
}

@RunWith(SpringRunner.class)
@SpringBootTest
public class UserControllerTest {
    @Autowired
    private WebApplicationContext webApplicationContext;
    private MockMvc mockMvc;

    @Before
    public void setUp() {
        mockMvc = MockMvcBuilders.webAppContextSetup(webApplicationContext).build();
    }

    @Test
    public void getUser() {
        mockMvc.perform(get("/v1/users/1")
                .accept(MediaType.APPLICATION_JSON_UTF8))
                .andExpect(status().isOk())
           .andExpect(content().string(containsString("\"name\":\"lyTongXue\"")));
    }
}
```

```java
// 异常
@Test(expected = NullPointerException.class)
public void whenExceptionThrown_thenExpectationSatisfied() {
    String test = null;
    test.length();
}
```
```java
// 修改私有变量
Student {
  String name;
}
Student s;
Field field = s.getClass().getDeclaredField("name");
field.setAccessible(true);
field.set(s, "andrew");
```

## 增强spring的UT
* [注解](http://www.2cto.com/kf/201302/189970.html)
* [注解2](http://www.codeweblog.com/%E5%A2%9E%E5%BC%BAspring-junit%E6%B5%8B%E8%AF%95%E6%A1%86%E6%9E%B6%E7%9A%84beforeclass%E5%92%8Cafterclass%E5%8A%9F%E8%83%BD/)

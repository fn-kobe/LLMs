

@[TOC](文章目录)

---

# 目录


# 一、AI大模型
## 1.1、AI大模型概念
AI 大模型是指具有高参数量（通常数以亿计乃至千亿以上）、深层网络结构、以及在海量数据上预训练的深度学习模型。其核心优势在于：

**①强泛化能力**：通过大规模预训练，模型具备更好的迁移学习能力。
**②多任务适应性**：同一模型可通过微调（fine-tuning）完成不同下游任务。
**③灵活扩展**：可通过模型压缩、蒸馏、切片等技术适配不同部署场景。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2ce127b81b1e447cb620eb62d802e212.png)
## 1.2、大模型的分类
### 1.2.1、按模态（Modality）分类
**①文本模型**：如 GPT、BERT 系列，擅长自然语言理解与生成。

**②图像模型**：如 ViT、Swin Transformer，专注于视觉识别与生成。

**③多模态模型**：如 CLIP、DALL·E、GPT-4V，将文本、图像、音频等多种模态融合处理。

### 1.2.2、按开源性分类

**①开源大模型**：如 LLaMA、Bloom，代码与权重可公开获取，便于二次开发及本地部署。

**②闭源/商用大模型**：如 OpenAI GPT、Anthropic Claude，通常通过 API 调用，受限于使用条款与计费模式。

### 1.2.3、按规模（Scale）分类

**①中小型大模型**（数亿~数十亿参数）：推理成本较低，适合资源受限场景。

**②超大规模模型**（百亿~千亿+参数）：性能更优，但对算力和内存需求高，适合云端部署。

### 1.2.4、按用途（Application）分类

**①通用对话/写作**：如 GPT 系列，侧重语言生成与交互。

**②专业领域**：如 BioGPT（生物医药）、LegalBERT（法律文本），针对垂直领域优化。

**③代码辅助**：如 Codex、CodeGeeX，专注编程与代码生成。

**④图像生成与编辑**：如 Stable Diffusion、Midjourney，生成高质量视觉内容。


# 二、接入大模型

## 2.1、使用大模型的两种途径

在实际开发过程中，使用AI大模型主要有两种途径：云服务与自部署，各有优缺点。

### 2.1.1、云服务

- **无需基础设施投入**：直接调用第三方厂商已部署好的大模型服务，无需考虑服务器、GPU 等硬件。  
- **按需付费**：无需前期大量基础设施投入，按调用量或时长计费。  
- **高可用 & 低维护**：服务可随时可用，厂商负责运维与扩缩容。  
- **自动更新**：即时获取最新版本的模型能力。  
- **安全合规**：通常具备完善的安全措施与合规保障。  
### 2.1.2、自部署

- **数据全控 & 高隐私**：所有数据流在本地或私有云，满足严苛的数据安全需求。
- **高度定制化**：可根据业务场景微调、剪枝或二次开发模型。  
- **无网络延迟**：适合对响应速度和离线能力有严格要求的场景。
- **一次性成本高**：需采购硬件、搭建集群，并由专业团队维护。
- **企业级场景优选**：适合对合规、审计、专属运维有严格要求的项目。

 **选型建议**  
- 个人开发者或中小团队：优先考虑 **云服务**，快速上线，降低维护成本。
 - 对数据安全、定制化要求高的企业级应用：可选择 **自部署**，获得最大化控制权 。通过Ollama本地部署，部署教程参考我之前写的博客链接：[Ollama部署](https://blog.csdn.net/weixin_44262492/article/details/145450539?spm=1001.2014.3001.5502)。
## 2.2、接入大模型的 3 种方式

在项目中使用 AI 大模型时，可选择以下三种接入方式，各有优劣和适用场景。

### 2.2.1、AI 应用平台接入

通过云服务商提供的一站式 AI 应用平台，快速构建并调用大模型能力。  
- **特点**  
  - 平台提供从模型调用到应用构建的全流程支持  。
  - 无需关心底层算力与运维，一键启动  。
- **示例**  
  - [阿里云百炼（Alibaba Cloud TiDE）](https://bailian.console.aliyun.com/?tab=model#/model-market)：一站式大模型开发与应用构建平台，支持界面化操作和自动化训练、部署。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7b8a4536385e4e6f8c8cb7ec6e2052d7.png)

### 2.2.2、AI 软件客户端接入

使用桌面或 Web 客户端软件，即可获得大模型交互和生产力工具。推荐两款使用较多的客户端：  
1. **[Cherry Studio](https://www.cherry-ai.com/)**  
   - 多模型对话、知识库管理 。
   - AI 绘画、翻译等功能一体化。  
   - 高度自定义界面与强扩展能力。
   ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7270d0db9ca4406c8d8a3eb31dae93d4.png)
  
2. **[Cursor](https://www.cursor.com/)**  
   - 以 AI 为核心的编程开发工具。  
   - 快速生成项目代码，智能理解并补全代码。  
   - 提供代码库导航与建议，提升开发效率。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c265507ef8c44d5bbb23a088ca98ccd0.png)

## 2.3、程序调用 AI 大模型

在实际开发中，有多种方式可以在应用程序中调用 AI 大模型。下面介绍 4 种主流接入方式，并以阿里云百炼平台（Paodian）Java SDK 为示例。

### 2.3.1、SDK 接入
**描述**
- 使用官方提供的软件开发工具包（SDK），最直接的集成方式。  
- 支持语言：Java、Python、Go 等。
- 选择SDK版本时，在Maven仓库查看最新的版本号。链接如下：[Maven仓库信息](https://mvnrepository.com/artifact/com.alibaba/dashscope-sdk-java)

**步骤**
- 1、pox.xml引入阿里云灵积SDK依赖。

```
<!-- https://mvnrepository.com/artifact/com.alibaba/dashscope-sdk-java -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>dashscope-sdk-java</artifactId>
    <version>2.19.1</version>
</dependency>
```

- 2、在[阿里云百炼平台](https://bailian.console.aliyun.com/?tab=model#/model-market)申请API-Key ，千万不要暴露。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/dd5bc7739fc44e3faa31cce719bdb60c.png)

- 3、选择合适的模型进行调用，点击模型、api参考、找到DashScope、选择Java代码接入。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a57615d62d744954b560bbb467e6f3c8.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ef5d97bde2ca4adea12ed068d4739f3b.png)

- 4、测试程序。执行成功，包含Token数等信息。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/f9e954adb8514045a5cf4bb47dd7ad83.png)
**优点**
- 简洁易用，一步到位。  
- 自动处理鉴权、序列化、重试等细节。

### 2.3.2、HTTP 接入

 **描述**
- 通过 REST API 直接发送 HTTP 请求调用模型。  
- 适用于任意语言和平台。

**步骤**
- 1、点击模型、api参考、找到DashScope、选择curl代码接入。特别说明：curl是检验http相应的工具。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8ee256fa58d7409f90347549be8b6503.png)
- 2、通过AI工具将上述请求转换为 hutool 工具类的请求代码。

```
package com.funian.agent.demo.invoke;

import cn.hutool.http.HttpRequest;
import cn.hutool.json.JSONObject;
import cn.hutool.json.JSONUtil;

/**
 * @Auther FuNian
 * @Major Computer Software
 */

/**
 * HTTP 方式调用 AI
 */
public class HttpAiInvoke {

    public static void main(String[] args) {
        // API密钥
        String apiKey = TestApiKey.API_KEY;

        // 构建请求URL
        String url = "https://dashscope.aliyuncs.com/api/v1/services/aigc/text-generation/generation";

        // 构建请求JSON数据
        JSONObject inputJson = new JSONObject();
        JSONObject messagesJson = new JSONObject();

        // 添加系统消息
        JSONObject systemMessage = new JSONObject();
        systemMessage.set("role", "system");
        systemMessage.set("content", "You are a helpful assistant.");

        // 添加用户消息
        JSONObject userMessage = new JSONObject();
        userMessage.set("role", "user");
        userMessage.set("content", "你好，我是爱健身的大学生，如何进行科学健身？");

        // 组装messages数组
        messagesJson.set("messages", JSONUtil.createArray().set(systemMessage).set(userMessage));

        // 构建参数
        JSONObject parametersJson = new JSONObject();
        parametersJson.set("result_format", "message");

        // 构建完整请求体
        JSONObject requestJson = new JSONObject();
        requestJson.set("model", "qwen-plus");
        requestJson.set("input", messagesJson);
        requestJson.set("parameters", parametersJson);

        // 发送请求
        String result = HttpRequest.post(url)
                .header("Authorization", "Bearer " + apiKey)
                .header("Content-Type", "application/json")
                .body(requestJson.toString())
                .execute()
                .body();

        // 输出结果
        System.out.println(result);
    }
}

```
 **优点**
- 灵活，不依赖特定 SDK。  
- 易于与微服务架构集成。

### 2.3.3、Spring AI

**描述**
- 基于 Spring 生态的 AI 调用框架。  
- 提供 Spring Bean 封装，可通过依赖注入快速调用大模型。
- **跨供应商可移植 API 支持**  
  适用于聊天、文本转图像和嵌入模型，支持同步与流式调用，并可访问各供应商特定功能。  
- **多模型供应商兼容**  
  支持 Anthropic、OpenAI、微软、亚马逊、谷歌、Ollama 等主流厂商，涵盖聊天、补全、嵌入、文本转图像、音频转录、文本转语音等多种模型类型。  
- **结构化输出**  
  将模型输出映射为 POJO（普通 Java 对象），方便业务代码直接消费。  
- **向量数据库集成**  
  支持 Apache Cassandra、Azure Cosmos DB、Azure Vector Search、Chroma、Elasticsearch、GemFire、MariaDB、Milvus、MongoDB Atlas、Neo4j、OpenSearch、Oracle、PostgreSQL/PGVector、Pinecone、Qdrant、Redis、SAP Hana、Typesense、Weaviate 等。  
- **跨向量存储可移植 API**  
  包括新颖的类 SQL 元数据过滤 API，简化检索层开发。  
- **工具/函数调用**  
  允许模型在运行时调用客户端工具和函数，根据上下文动态获取所需信息并执行操作。  
- **可观测性**  
  提供与 AI 相关操作的监控与指标采集。  
- **文档 ETL 框架**  
  适用于大规模文档与数据处理场景。  
- **AI 模型评估工具**  
  帮助评估生成内容质量并防范幻觉（hallucination）。  
- **Spring Boot 自动配置与启动器**  
  支持 AI 模型和向量存储的一键引入与管理。  
- **ChatClient API**  
  类似 WebClient/RestClient 的流式通信 API，用于与聊天模型高效交互。  
- **Advisors API**  
  封装常见生成式 AI 模式，将请求发送到 LLM 并解析返回结果，提供跨模型与跨用例的统一调用接口。  
- **对话记忆与检索增强生成（RAG）支持**  
  内置对话状态管理与检索-生成流程，简化 RAG 应用开发。  


**步骤**
- 1、使用Spring AI alibaba，pom.xml引入依赖，Maven中央仓库下载版本。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8e653024fce74b0a9560147edff6346f.png)

```
<dependency>
    <groupId>com.alibaba.cloud.ai</groupId>
    <artifactId>spring-ai-alibaba-starter</artifactId>
    <version>1.0.0-M6.1</version>
</dependency>

```

```
<repositories>
  <repository>
    <id>spring-milestones</id>
    <name>Spring Milestones</name>
    <url>https://repo.spring.io/milestone</url>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
  </repository>
</repositories>

```

- 2、编写yml配置。

```
spring:
  application:
    name: Agent
  ai:
    dashscope:
      api-key: ${AI_DASHSCOPE_API_KEY}
      chat:
        options:
          model: qwen-plus

```

- 3、使用charmodel方式注入模型，模型参数为dashscopeChatModel，之后会自动注入大模型，实现CommandLineRunner接口，启动SpringBoot项目时会单次执行该类的run方法，从而达到测试效果。

```
@Component
public class SpringAiAiInvoke implements CommandLineRunner {

    @Resource
    private ChatModel dashscopeChatModel;

    @Override
    public void run(String... args) throws Exception {
        AssistantMessage output = dashscopeChatModel.call(new Prompt("你好，我是爱健身的大学生"))
                .getResult()
                .getOutput();
        System.out.println(output.getText());
    }
}

```
- 4、测试成功。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/012ae600b55b4c1286b6a0e9a872d20c.png)

**优点**
- 与现有 Spring Boot 项目无缝集成。  
- 支持配置化管理与自动化监控。

### 2.3.4、LangChain4j

**描述**
- 专注于构建 LLM 应用的 Java 框架。  
- 提供丰富的 AI 调用组件、链式调用和流水线支持。

**步骤**
- 1、pom.xml引入依赖。  

```
public class LangChainAiInvoke {

    public static void main(String[] args) {
        ChatLanguageModel qwenModel = QwenChatModel.builder()
                .apiKey(TestApiKey.API_KEY)
                .modelName("qwen-max")
                .build();
        String answer = qwenModel.chat("我是爱健身的大学生");
        System.out.println(answer);
    }
}

```

- 2、参考官方代码撰写示例，[地址如下](https://docs.langchain4j.dev/integrations/language-models/dashscope/)：https://docs.langchain4j.dev/integrations/language-models/dashscope/。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c93f6523133d40579093767755287650.png)

```
public class LangChainAiInvoke {

    public static void main(String[] args) {
        ChatLanguageModel qwenModel = QwenChatModel.builder()
                .apiKey(TestApiKey.API_KEY)
                .modelName("qwen-max")
                .build();
        String answer = qwenModel.chat("我是爱健身的大学生");
        System.out.println(answer);
    }
}

```
- 3、测试成功。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c9e24960658540b7abe3226b700ab715.png)

**优点**
- 高度模块化，适合复杂业务场景。  
- 内置常见 LLM 操作（prompt 模板、缓存、并发控制等）。
### 2.3.5、接入方式对比

以下是 4 种 AI 大模型接入方式的优缺点对比：

| 接入方式       | 优点                                                                                   | 缺点                                                                                   | 适用场景                                                |
|--------------|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-------------------------------------------------------|
| **SDK 接入**   | - 类型安全，编译时检查<br/>- 完善的错误处理<br/>- 通常有详细文档，性能优化好                        | - 依赖特定版本，可能增加项目体积<br/>- 语言受限                                          | - 需要深度集成<br/>- 单一模型提供商<br/>- 对性能要求高               |
| **HTTP 接入**  | - 无语言限制，不增加额外依赖<br/>- 灵活性高                                              | - 需要手动处理错误、序列化/反序列化<br/>- 代码冗长                                       | - SDK 不支持的语言<br/>- 简单原型验证<br/>- 临时性集成               |
| **Spring AI** | - 统一抽象接口，易于切换模型提供商<br/>- 与 Spring 生态完美融合<br/>- 提供高级功能               | - 增加额外抽象层，可能不支持某些模型特性<br/>- 版本仍在快速迭代中                           | - Spring 应用<br/>- 需要支持多种模型<br/>- 需高级 AI 功能            |
| **LangChain4j** | - 提供完整 AI 应用工具链，支持复杂工作流<br/>- 丰富的组件和工具，适合构建 AI 代理                 | - 学习曲线较陡，文档相对较少<br/>- 高度抽象可能引入性能开销                             | - 构建复杂 AI 应用<br/>- 需要链式操作、RAG 应用开发                  |



**推荐**：  
- 我个人更倾向于 **Spring AI**，因为它属于 Spring 生态，简单易用、资源丰富，能满足绝大多数 AI 项目的开发需求。  
- 无论选择哪种接入方式，都建议先用简单的测试用例验证接入是否成功，再进行复杂功能开发。

# 三、Spring AI 接入ollama部署的本地大模型
**描述**
- 链接：[安装Ollama本地Deepseek大模型](https://blog.csdn.net/weixin_44262492/article/details/145450539?spm=1001.2014.3001.5502)。  
- 本地部署大模型保证更好的数据隐私控制、无需网络即可调用。

**步骤**
- 1、检验大模型是否安装成功、pom.xml引入依赖。  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/02bf9974968b49e3bf8c43c114206ee4.png)

```
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-ollama-spring-boot-starter</artifactId>
    <version>1.0.0-M6</version>
</dependency>
```

```
<repositories>
  <repository>
    <id>spring-milestones</id>
    <name>Spring Milestones</name>
    <url>https://repo.spring.io/milestone</url>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
  </repository>
</repositories>

```

- 2、编写yml配置。

```
spring:
  ai:
    ollama:
      base-url: http://localhost:11434
      chat:
        model: deepseek-r1:7b
```
3、编写测试代码。

```
@Component
public class OllamaAiInvoke implements CommandLineRunner {

    @Resource
    private ChatModel ollamaChatModel;

    @Override
    public void run(String... args) throws Exception {
        AssistantMessage output = ollamaChatModel.call(new Prompt("你好，我是爱健身的大学生"))
                .getResult()
                .getOutput();
        System.out.println(output.getText());
    }
}

```
4、启动项目测试，显示成功。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/da7b5aaf3e3f4f8e9c283c0b80beb099.png)

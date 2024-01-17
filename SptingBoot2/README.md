SpringBoot2
==================
- [SpringBoot2](#springboot2)


* * *
<h2 id="ch01">SpringBoot2入門</h2>
 參考文件: <a href="https://docs.spring.io/spring-boot/docs/2.3.4.RELEASE/reference/htmlsingle/">Reference Documentation</a> 

    *   https://docs.spring.io/spring-boot/docs/{SpringBoot版本}/reference/htmlsingle/
       
    *   SpringBoot版本可選擇current或指定特定版號。

<h2 id="ch01-1">系統要求</h2>

    *   Java8&兼容java14
    *   Maven 3.3+
<h2 id="ch01-2">maven設置</h2>

設置setting.xml的內容。 ( apache-maven-x.x.x/conf/setting.xml )

    *   預設maven專案使用jdk1.8
    *   設置遠端倉庫


```xml
<profiles>
    <profile>
        <id>jdk-1.8</id>
        <activation>
            <activeByDefault>true</activeByDefault>
            <jdk>1.8</jdk>
        </activation>
        <properties>
            <maven.compiler.source>1.8</maven.compiler.source>
            <maven.compiler.target>1.8</maven.compiler.target>
            <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
        </properties>  
    </profile>
</profiles>
    
</mirrors>
    <mirror>
        <id>nexus-maven</id>
        <mirrorOf>central</mirrorOf>
        <name>Nexus maven</name>
        <url>https://repo1.maven.org/maven2/</url>
    </mirror>
</mirrors>
```

<h2 id="ch01-3">HelloWorld</h2>

    *   需求:瀏覽器發送 /hello 請求，回覆 Hello, Spring Boot 2
<h2 id="ch01-4">創建Maven工程</h2>

<h2 id="ch01-5">引入依賴</h2>
pom.xml增加SpringBoot的基本配置。

```xml
<!-- SpringBoot-parent -->
<parent>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-parent</artifactId>
	<version>2.3.4.RELEASE</version>
</parent>
<dependencies>
	<!-- spring-boot-starter-web -->
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>
```
<h2 id="ch01-6">編寫主程式</h2>

```java
/**
 * 主程序
 * @SpringBootApplication : 宣告該類為SpringBoot的主類
 */
@SpringBootApplication
public class Application {
	public static void main(String[] args) {
		SpringApplication.run(Application.class, args);
	}
}
```
<h2 id="ch01-6">編寫商業邏輯</h2>

```java
@RestController
public class HelloController {

	@RequestMapping("/hello")
	public String handle01() {
		return "Hello, Spring Boot 2";
	}
}
```
<h2 id="ch01-7">執行</h2>
直接運行主程序類main方法

<h2 id="ch01-9">簡化配置</h2>
application.properties

<h2 id="ch01-9">簡化部署</h2>

省去過往安裝部署Tomcat的相關事項，透過引入SpringBoot的插件,將項目打包為jar包,即可在主機上運行。

```xml
<build>
	<plugins>
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
		</plugin>
	</plugins>
</build>
```

        java -jar XXXXXXX.jar


# spring web docker

* docker 文件夹复制至根目录
    
    webapps （web目录）
    Dockerfile （基于 tomcat:8.0 生成docker镜像）
    
* pom.xml 增加插件
  ```
  <plugins>
      <plugin>
          <artifactId>maven-war-plugin</artifactId>
          <configuration>
              <outputDirectory>${basedir}/docker/webapps</outputDirectory>
          </configuration>
      </plugin>
      <plugin>
          <groupId>com.spotify</groupId>
          <artifactId>docker-maven-plugin</artifactId>
          <version>0.4.13</version>
          <configuration>
              <imageName>${project.name}:${project.version}</imageName>
              <!--Dockerfile文件位置-->
              <dockerDirectory>${basedir}/docker</dockerDirectory>
          </configuration>
      </plugin>
  </plugins>
  ```
  
* 执行 `mvn clean package docker:build`
 
  若镜像需要发布则执行 `mvn clean package docker:build -DpushImage`
  
* 执行 `docker run -p 8080:8080 -it ${project.name}:${project.version}`

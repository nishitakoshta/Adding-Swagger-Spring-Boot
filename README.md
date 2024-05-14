# Adding-Swagger-Spring-Boot(3.x)
- [Reference Doc](https://springdoc.org/)
- Add `springdoc-openapi-starter-webmvc-ui` depency in your project.
  ```
  implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.2.0'
  ```
- Add these two in application.properties
  ```
  #OpenApi
  springdoc.packagesToScan=com.personal.jobportal.jobportalproject.controller
  springdoc.pathsToMatch=/api/v1/users/**, /api/v1/jobs/**, /api/v1/questions/**, /api/v1/applications/**
  ```
- Run your project.
- Create config package/class for swagger configuration 
```
@Configuration
public class SwaggerConfig {
        String bearerScheme ="bearerScheme";
        @Bean
        public OpenAPI springShopOpenAPI() {
                return new OpenAPI()
                        .addSecurityItem(new SecurityRequirement()
                                .addList(bearerScheme))
                        .components(new Components()
                                .addSecuritySchemes(bearerScheme, new SecurityScheme()
                                        .name(bearerScheme)
                                        .type(SecurityScheme.Type.HTTP)
                                        .bearerFormat("JWT")
                                        .scheme("bearer")
                                )
                        )
                        .info(new Info().title("SpringShop API")
                                .description("Spring shop sample application")
                                .version("v0.0.1")
                                .license(new License().name("Apache 2.0")));
        }
}
```

# Adding-Swagger-Spring-Boot(3.x)
- [Reference Doc](https://springdoc.org/)
- Add `springdoc-openapi-starter-webmvc-ui` depency in your project.
- Run your project.
- Create config package/class for swagger configuration 
```
@OpenAPIDefinition(
        info = @Info(
                title = "Doc Title",
                description = "Description",
                version = "v1"
        ),
        servers = {
                @Server(
                   description = "SeverName",
                        url = "ServerURL"
                )
        },
        security = @SecurityRequirement(
                name = "authentication"
        )
)
@SecurityScheme(
        name = "authentication",
        in = SecuritySchemeIn.HEADER,
        type = SecuritySchemeType.HTTP,
        bearerFormat = "JWT",
        scheme = "bearer"
)
public class SwaggerConfig {
}
```

# Spring
Estudando Spring Framework, um framework open source para Java.


## Anotações:

### @Value

É uma forma de injetar valores em classes gerenciadas pelo Spring, pode ser aplicado em atributos, parâmetros do construtor ou métodos.

Pode ser passado diretamente o valor.

```java
@Value("Silvano")
private String name;
```

Ou podemos colocar uma variável e atribuir seu valor em um arquivo properties que deve ser indicado na classe com a anotação @PropertySource("classpath:values.properties"), este arquivo properties esta dentro de resources.

Exemplo de arquivo properties:

```java
name=Silvano
sobrenome=Araujo
notas=8,6,7,5
```

Então quando for preciso usar o valor, devemos usar a anotação @PropertySource("classpath:values.properties") acima da classe
e acima do atributo deve ser colocado a anotação @Value com o nome da variável.



```java
@Configuration
@PropertySource("classpath:values.properties")
public class Cliente {

  @Value("name")
  private String name;
  
  @Autowired
  public void setNotas(@Value("#{'${notas}'.split(',')}") List<String> values) {
    this.values.addAll(values);
  }
  
}
  
```


Referencia https://www.baeldung.com/spring-value-annotation

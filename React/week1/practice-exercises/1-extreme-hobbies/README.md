# Passatempos extremos

Não há nada melhor do que alguns esportes radicais para fazer o sangue bombear.

Dê uma olhada no seguinte:

``` js
const hobbies = ["Surf", "Escalada", "Bicicleta de montanha", "Breakdancing"];
```

1. Execute `create-react-app` nesta pasta para criar seu ambiente
2. Crie 2 componentes funcionais: `<HobbyList>` e `<Hobby>`
3. Coloque a variável `hobbies` no componente `<HobbyList>`.
4. Na instrução `return` de `<HobbyList>` use a função `map()` para retornar uma instância de `<Hobby>` para cada hobby no array
5. Passe a string hobby como um `prop` para o componente `<Hobby>` (não se esqueça de adicionar o prop `key` também!)
6. Teste se funciona importando-o para o componente de nível superior, que neste caso é `<App>`

# Galeria de fotos de cães

Vamos fazer uma galeria aleatória de fotos de cachorros!

Neste exercício, usaremos o seguinte endpoint de API: `https://dog.ceo/api/breeds/image/random`

1. Crie 3 componentes funcionais: `<DogGallery>`, `<DogPhoto>` e `<Button>`
2. Dentro de `<DogGallery>` crie uma variável de estado chamada `dogPhotos` (inicialize com o valor `[]`) e o manipulador de estado `setDogPhotos`
3. Dentro (antes da instrução return) também crie uma função chamada `getDogPhoto`. O objetivo desta função é fazer uma chamada de API para `https://dog.ceo/api/breeds/image/random`. Você pode usar `fetch` ou `axios`. No final da função, envie o novo `URL da imagem do cão` para a variável de estado do array `dogPhotos` usando `setDogPhotos`
4. Dentro do componente `<Button>`, crie um `<button>` que tenha o texto "Get a dog!" e atributo `onClick`
5. Passe a função `getDogPhoto` para `<Button>`
6. Dentro de `<DogGallery>` retorne todos os cães armazenados no array `dogPhotos` usando a função `map()`. Passe cada `dogPhoto` para uma instância de `<DogPhoto>`.
7. No entanto, quando ainda não houver cães na matriz, certifique-se de exibir a mensagem "Pegue seu primeiro cachorro clicando no botão!"
8. Verifique seus componentes importando-os para o componente de nível superior, que é `<App>`

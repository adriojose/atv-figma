<script setup>
 
  import { ref, computed } from 'vue'

const pagina = ref(0)
function hmpg() {
  pagina.value = 0 
}
function carrinho() {
  pagina.value = 1
}

// Lista de livros (poderia vir de um JSON/fetch depois)
const livros = ref([
  { id: 1, titulo: "Chain of Iron: Volume 2", autor: "Cassandra Clare", preco: 23.24, img: "/livro.png" },
  { id: 2, titulo: "Chain of Thorns", autor: "Cassandra Clare", preco: 23.24, img: "/livro2.png" },
  { id: 3, titulo: "City of fallen ", autor: "Cassandra Clare", preco: 13.94, img: "/livro3.png"},
  { id: 4, titulo: "Nona the Ninth", autor: "Cassandra Clare", preco: 16.84, img: "/livro4.png"},
  { id: 5, titulo: "Harlem Shuffle", autor: "Colson Whitehead", preco: 26.92, img: "/livro5.png"},
  { id: 6, titulo: "Two Old Women", autor: "Velma Wallis", preco: 13.95, img: "/livro6.png"},
  { id: 7, titulo: "Carrie Soto Is Back", autor: "Taylor Jenkins Reid", preco: 26.04, img: "/livro7.png"},
  { id: 8, titulo: "Book Lovers", autor: "Emily Henry", preco: 15.81, img: "/livro8.png"},
  
])

// Carrinho reativo
const carrinhoLivros = ref([])

function adicionarAoCarrinho(livro) {
  const existente = carrinhoLivros.value.find(item => item.id === livro.id)
  if (existente) {
    existente.quantidade += 1
  } else {
    carrinhoLivros.value.push({ ...livro, quantidade: 1 })
  }
}

function aumentarQuantidade(livro) {
  livro.quantidade += 1
}

function diminuirQuantidade(livro) {
  if (livro.quantidade > 1) {
    livro.quantidade -= 1
  } else {
    carrinhoLivros.value = carrinhoLivros.value.filter(item => item.id !== livro.id)
  }
}
function limparCarrinho() {
  carrinhoLivros.value = []
}

const total = computed(() => {
  return carrinhoLivros.value.reduce((acc, livro) => acc + livro.preco * livro.quantidade, 0).toFixed(2)
})


</script>
<template>
  <body>
    
    <main>
      <header>
        
  <nav class="navegacao">
   
     <ul>
        <li>
           <p>
             <a @click="hmpg()" class="ifbooks">IFbooks</a>
           </p>
        </li>
        <div class="pauzinho1"></div>
        <li>
          <span>Apreço a  leitura</span>
        </li>
        <div class="barra-pesquisa">Pesquisar</div>
        <li>
            <a href="#">Termos</a>
        </li>
        <li>
          <a href="#">Equipe</a>
        </li>
        <li>
          <a href="#">Envio</a>
        </li>
        <li>
          <a href="#">Devoluções</a>
        
        </li>
     
      <div class="menu-icones">
          <a @click="carrinho()"><img src="/carrinho.png" alt="carrinho" class="icon" /></a>
      <div class="pauzinho"></div>
      <img src="/Heart.png" alt="coração" class="icon" />
      <div class="pauzinho"></div>
      <img src="/User.png" alt="usuário" class="icon" />
    </div>
     </ul> 
  </nav>
</header>
    <div v-if="pagina == 0">
          <section>
            <div>
              <h4>
                Autor de abril
              </h4>    
              <h1>
                  Eric-Emanuel Schmitt
              </h1>
                <p>
                  Eric-Emmanuel Schmitt has been awarded more than 20 <br>  literary prizes and distinctions, and in 2001 he received the <br>  title of Chevalier des Arts et des Lettres. His books have been <br>  translated into over 40 languages.
                </p>
                <button>Acessar página do livro</button>
            </div>
            <div class="livro">
              <img src="/book.png" alt="book.png">
            </div>
          </section>
          <section class="borda">
                <div class="selos">
                  <img src="/Truck.png" alt="truck.png" class="selo">
                  <div class="texto">Frete grátis para SC</div>
                  <div class="traco"></div>
                  <img src="/Star.png" alt="star.png" class="selo">
                  <div class="texto">Livros recomendados</div>
                  <div class="traco"></div>
                  <img src="/Book open.png" alt="book.png" class="selo">
                  <div class="texto2">Mais vendidos</div>   
                </div>
          </section>
          <div class="borda2"></div>
          
                <h2>
                    Lançamentos
                </h2>
                <div class="container">
  <div class="item" v-for="livro in livros" :key="livro.id">
    <img :src="livro.img" :alt="livro.titulo" />
    <h3>{{ livro.titulo }}</h3>
    <p>{{ livro.autor }}</p>
    <p class="preco">R${{ livro.preco.toFixed(2) }}</p>
    <button @click="adicionarAoCarrinho(livro)">Comprar</button>
  </div>
</div>
          
              </div>


              <div class="little-car" v-if="pagina == 1">
                <h2 class="titulo-carrinho">Carrinho</h2>
                <div class="livros-carrinho">
                  <h3>Titulo</h3>
                  <h3>Quantidade</h3>
                  <h3>Subtotal</h3> 
                </div>
                <div class="borda-carrinho"></div> 
                <div v-for="item in carrinhoLivros" :key="item.id" class="valor-total">
  <!-- Coluna 1: título e autor -->
  <div class="coluna">
    <img :src="item.img" />
    <h3>{{ item.titulo }}</h3>
    <p class="autor">{{ item.autor }}</p>
    <p class="preco">R${{ item.preco }}</p>
  </div>
      
  <!-- Coluna 2: botões de quantidade -->
  <div class="coluna">
    <div class="quantidade">
      <button @click="diminuirQuantidade(item)">-</button>
     <span>{{ item.quantidade }}</span> 
      <button @click="aumentarQuantidade(item)">+</button>
    </div>
  </div>
 
  <!-- Coluna 3: subtotal -->
  <div class="coluna">
    <p class="preco2">R${{ (item.preco * item.quantidade).toFixed(2) }}</p>
  </div>
</div>


  <div class="total-final">
    <h3 class="valor-final">Total: R${{ total }}</h3>
    <button @click="limparCarrinho" class="botao-limpar">Limpar carrinho</button>
  </div>
</div>
    </main>     
    <footer>
      <div class="contato">
        <div class="footer-titulo">IFbooks</div>
        <p><i class="fa-brands fa-square-facebook"></i><i class="fa-brands fa-instagram"></i><i class="fa-brands fa-square-twitter"></i></p>
      </div>  
        <div class="contato2">
          <p>Contato</p>
        <p>+55 47 40045263</p>
        <p>8h às 23h - Seg a Sex</p>
        <p>contato@ifbooks.com</p>
        <p class="cartoes"><img src="/paipal 1.png" alt="paipal 1"> <img src="/MasterCard 1.png" alt="mastercard1"> <img src="" alt=""> <img src="/VISA 1.png" alt="visa"></p>
        </div>
        
    </footer>
    <div class="footer-borda"></div>
    <div class="footer-direitos">
      <p>© Alguns direitos reservados. IFbooks 2025.</p>
    </div>
   
    
   
  </body>

</template>

<style scoped>

</style>

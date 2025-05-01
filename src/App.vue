<script setup>
import { ref } from 'vue';

  const pagina = ref(0)
  function hmpg(){
    pagina.value = 0 
  }
  function carrinho(){
    pagina.value = 1
  }




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
          <a @click="carrinho()"><img src="@/assets/carrinho.png" alt="carrinho" class="icon" /></a>
      <div class="pauzinho"></div>
      <img src="@/assets/Heart.png" alt="coração" class="icon" />
      <div class="pauzinho"></div>
      <img src="@/assets/User.png" alt="usuário" class="icon" />
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
              <img src="/src/assets/book.png" alt="book.png">
            </div>
          </section>
          <section class="borda">
                <div class="selos">
                  <img src="/src/assets/Truck.png" alt="truck.png" class="selo">
                  <div class="texto">Frete grátis para SC</div>
                  <div class="traco"></div>
                  <img src="/src/assets/Star.png" alt="star.png" class="selo">
                  <div class="texto">Livros recomendados</div>
                  <div class="traco"></div>
                  <img src="/src/assets/Book open.png" alt="book.png" class="selo">
                  <div class="texto2">Mais vendidos</div>   
                </div>
          </section>
          <div class="borda2"></div>
          
                <h2>
                    Lançamentos
                </h2>
               <div class="container">
                <div class="item">
                  <img src="/src/assets/livro.png" alt="livro.png">
                  <h3>Chain of Iron: Volume 2</h3>
                  <p>Cassandra Clare</p>
                  <p class="preco">R$23.24</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro2.png" alt="livro2.png">
                  <h3>Chain of Thorns</h3>
                  <p>Cassandra Clare</p>
                   <p class="preco">R$23.24</p>
                  <button><i class="fa-solid fa-cart-shopping"></i> Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro3.png" alt="livro3.png">
                  <h3>City of Fallen Angels</h3>
                  <p>Cassandra Clare</p>
                  <p class="preco">R$13.94</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro4.png" alt="livro4.png">
                  <h3>Nona the Ninth</h3>
                  <p>Cassandra Clare</p>
                  <p class="preco">R$16.84</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro5.png" alt="livro5.png">
                  <h3>Harlem Shuffle</h3>
                  <p>Colson Whitehead</p>
                  <p class="preco">R$26.92</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro6.png" alt="livro6.png">
                  <h3>Two Old Women</h3>
                  <p>Velma Wallis</p>
                  <p class="preco">R$13.95</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro7.png" alt="livro7.png">
                  <h3>Carrie Soto Is Back</h3>
                  <p>Taylor Jenkins Reid</p>
                  <p class="preco">R$26.04</p>
                  <button>Comprar</button>
                </div>
                <div class="item">
                  <img src="/src/assets/livro8.png" alt="livro8.png">
                  <h3>Book Lovers</h3>
                  <p>Emily Henry</p>
                  <p class="preco">R$15.81</p>
                  <button>Comprar</button>
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
                <div class="valor-total">
                  <img src="/src/assets/livro.png" alt="livro.png">
                  <div class="descricao-carrinho">  
                  <h3>Chain of Iron: Volume 2</h3>
                  <p>Cassandra Clare</p>
                  <p class="preco">R$23.24</p>
                    </div>
                  
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
        <p class="cartoes"><img src="/src/assets/paipal 1.png" alt="paipal 1"> <img src="/src/assets/MasterCard 1.png" alt="mastercard1"> <img src="" alt=""> <img src="/src/assets/VISA 1.png" alt="visa"></p>
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

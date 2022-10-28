<template>
  <main class="container-fluid px-4 px-md-0">
    <HeaderView />
    <div class="row g-0">
      <div class="col-12">
        <section>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <h1>Catálogo de peliculas</h1>
              <p class="text-justify">
                Quieres conocer sobre las películas, compositores y álbumes, te invitamos a que selecciones una pelicula
                de nuestro catálogo para descubrirlo.
              </p>
            </div>
          </div>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <div class="row g-0 justify-content-center">
                  <div class="col-10 col-sm-6 col-md-4" v-for="pelicula in peliculas" :key="pelicula.id">
                    <div class="card m-3">
                      <img :src="`https://cms-una.000webhostapp.com/storage/uploads${pelicula.image.path}`" class="card-img-top" :alt="'Imagen ' + pelicula.title" />
                      <div class="card-body">
                        <h5 class="card-title">{{ pelicula.title }}</h5>
                        <p class="card-text">
                          {{pelicula.Sinopsis}}
                        </p>
                        <NuxtLink class="btn btn-primary" :to="`/peliculas/${pelicula._id}`">Ver detalle</NuxtLink>
                      </div>
                    </div>
                  </div>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>
    <FooterView />
  </main>
</template>
<script setup>
  const { data: peliculas } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/peliculas?fields={"id":true,"title":true,"Sinopsis": true, "image": true}`)
    console.log(peliculas);
</script>
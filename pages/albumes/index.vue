<template>
  <main class="container-fluid px-4 px-md-0">
    <HeaderView />
    <div class="row g-0">
      <div class="col-12">
        <section>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <h1>Catálogo de álbumes de peliculas</h1>
              <p class="text-justify">
                Conoce la información de los álbumes de las peliculas y sus compositores, te invitamos a que selecciones un álbum
                de nuestro catálogo para descubrirlo.
              </p>
            </div>
          </div>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <div class="row g-0 justify-content-center">
                  <div class="col-10 col-sm-6 col-md-4" v-for="album in albumes" :key="album.id">
                    <div class="card m-3">
                      <img :src="`https://cms-una.000webhostapp.com/storage/uploads${album.image.path}`" class="card-img-top" :alt="'Imagen ' + album.title" />
                      <div class="card-body">
                        <h5 class="card-title">{{ album.title }}</h5>
                        <p class="card-text">
                        </p>
                        <NuxtLink class="btn btn-primary" :to="`/albumes/${album._id}`">Ver detalle</NuxtLink>
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
  const { data: albumes } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/albumes?fields={"id":true,"title":true,"Sinopsis": true, "image": true}`)
    console.log(albumes);
</script>
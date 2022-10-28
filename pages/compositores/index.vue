<template>
  <main class="container-fluid px-4 px-md-0">
    <HeaderView />
    <div class="row g-0">
      <div class="col-12">
        <section>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <h1>Catálogo de compositores</h1>
              <p class="text-justify">
                Conoce la información de los compositores de las bandas sonoras de las peliculas y sus álbumes, te invitamos a que selecciones un compositor
                de nuestro catálogo para descubrirlo.
              </p>
            </div>
          </div>
          <div class="row g-0 justify-content-md-center">
            <div class="col-12 col-md-10 text-justify">
              <div class="row g-0 justify-content-center">
                  <div class="col-10 col-sm-6 col-md-4" v-for="compositor in compositores" :key="compositor.id">
                    <div class="card m-3">
                      <img :src="`https://cms-una.000webhostapp.com/storage/uploads${compositor.image.path}`" class="card-img-top" :alt="'Imagen ' + compositor.title" />
                      <div class="card-body">
                        <h5 class="card-title">{{ compositor.title }}</h5>
                        <p class="card-text">
                          {{compositor.Resumen}}
                        </p>
                        <NuxtLink class="btn btn-primary" :to="`/compositores/${compositor._id}`">Ver detalle</NuxtLink>
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
  const { data: compositores } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/items/compositores?fields={"id":true,"title":true,"Resumen": true, "image": true}`)
    console.log(compositores);
</script>
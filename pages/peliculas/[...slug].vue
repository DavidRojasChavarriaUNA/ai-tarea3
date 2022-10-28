<template>
    <main class="container-fluid px-4 px-md-0">
        <HeaderView />
        <div class="row g-0">
            <div class="col-12">
                <section>
                        <div class="row g-0 justify-content-md-center">
                            <div class="col-12 col-md-10 text-justify">
                                <h1>{{pelicula.title}}</h1>
                                <div class="row g-0 justify-content-center">
                                    <div class="col-8 col-md-4  text-center">
                                        <img class="img-fluid" :src="`https://cms-una.000webhostapp.com/storage/uploads${pelicula.image.path}`">
                                    </div>
                                    <div class="col-12 col-md-8 text-justify pt-3 ps-md-4">
                                        <h5>
                                            Banda sonora compuesta por:
                                            <ul>
                                                <li v-for="compositor in pelicula.compositores" :key="compositor._id">
                                                    <NuxtLink :to="`/compositores/${compositor._id}`">{{compositor._id}}</NuxtLink>
                                                </li>
                                            </ul>
                                        </h5>
                                        <h5>
                                            Album de la pelicula:
                                            <ul>
                                                <li>
                                                    <NuxtLink :to="'/albumes/'+pelicula.album.id">{{pelicula.album.nombre}}
                                                    </NuxtLink>
                                                    <NuxtLink :to="`/albumes/${pelicula.album._id}`">{{pelicula.album._id}}</NuxtLink>
                                                </li>
                                            </ul>
                                        </h5>
                                        <div v-html="pelicula.descripcion"></div>
                                    </div>
                                    <hr>
                                </div>
                            </div>
                        </div>
                        <div class="row g-0 justify-content-center mt-4">
                            <div class="col-12 col-md-10 text-justify">
                                <h3>Trailer de la película</h3>
                                <div class="containerVideo">
                                    <iframe :src="pelicula.trailer" title="YouTube video player" frameborder="0"
                                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                                        allowfullscreen class="video"></iframe>
                                </div>
                                <br>
                                <NuxtLink to="/peliculas">Regresar</NuxtLink>
                            </div>
                        </div>
                </section>
            </div>
        </div>
        <FooterView />
    </main>
</template>
<script setup>
  const route = useRoute()
  const { data: pelicula, refresh: rPelicula } = 
    await useFetch(`https://cms-una.000webhostapp.com/api/content/item/peliculas/${route.params.slug}`)
  rPelicula()
  console.log("pelicula",pelicula);
</script>
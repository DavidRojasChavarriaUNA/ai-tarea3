<template>
    <main class="container-fluid px-4 px-md-0">
        <HeaderView />
        <div class="row g-0">
            <div class="col-12">
                <section>
                    <div class="row g-0 justify-content-md-center">
                        <div class="col-12 col-md-10 text-justify">
                            <h1>{{album.title}}</h1>
                            <div class="row g-0 justify-content-center">
                                <div class="col-8 col-md-4  text-center">
                                    <img class="img-fluid"
                                        :src="`https://cms-una.000webhostapp.com/storage/uploads${album.image.path}`">
                                </div>
                                <div class="col-12 col-md-8 text-justify pt-3 ps-md-4">
                                    <h5>Banda sonora compuesta por:</h5>
                                    <ul>
                                        <li v-for="compositor in album.compositores" :key="compositor._id">
                                            <NuxtLink :to="`/compositores/${compositor._id}`">{{compositor._id}}
                                            </NuxtLink>
                                        </li>
                                    </ul>
                                    <h5>Pelicula:</h5>
                                    <ul>
                                        <li v-for="pelicula in peliculas" :key="pelicula.id">
                                            <NuxtLink :to="'/peliculas/'+pelicula._id">
                                                {{pelicula.title}}
                                            </NuxtLink>
                                        </li>
                                    </ul>
                                    <h5>Discográfica</h5>
                                    <ul>
                                        <li>{{album.discografica}}</li>
                                    </ul>
                                    <h5>Duración</h5>
                                    <ul>
                                        <li>{{album.duracion}}</li>
                                    </ul>
                                </div>
                                <hr class="mt-5">
                            </div>
                            <div class="row g-0 justify-content-center mt-4">
                                <div class="col-12 col-md-10 text-justify">
                                    <div v-html="album.descripcion"></div>
                                    <br>
                                    <NuxtLink to="/albumes">Regresar</NuxtLink>
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
    const route = useRoute()
    const {
        data: album,
        refresh: rAlbum
    } =
    await useFetch(`https://cms-una.000webhostapp.com/api/content/item/albumes/${route.params.slug}`)
    rAlbum()
    console.log("album", album);
    const {
        data: peliculas,
        refresh: rPeliculas
    } =
    await useFetch(
        `https://cms-una.000webhostapp.com/api/content/items/peliculas?filter={"album._id":"${route.params.slug}"}&fields={"id":true,"title":true}`
    )
    rPeliculas()
    console.log("peliculas", peliculas);
</script>
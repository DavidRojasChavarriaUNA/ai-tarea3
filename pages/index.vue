<template>
  <main class="container-fluid px-4 px-md-0">
    <HeaderView />
    <div class="row g-0">
      <div class="col-12">
        <section>
          <ContentDoc path="/indexfiles/musicacine" v-slot="{doc}">
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 text-justify">
                <ContentRenderer :value="doc" />
              </div>
            </div>
            <div class="row g-0 justify-content-md-center mb-4">
              <div class="col-12 col-md-10">
                <NuxtLink class="link-info fs-5" to="/peliculas">Ver nuestro catálogo de películas</NuxtLink>
              </div>
            </div>
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 col-lg-8 text-center">
                <img class="img-fluid" :src="doc.image">
                <br>
                <NuxtLink class="fs-6" :to="doc.linkArticuloImagen" target="_blank">{{doc.titleImage}}</NuxtLink>
              </div>
            </div>
          </ContentDoc>
        </section>
      </div>
    </div>
    <div class="row g-0 pt-5">
      <div class="col-12">
        <section>
          <ContentDoc path="/indexfiles/compositor" v-slot="{doc}">
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 text-justify">
                <ContentRenderer :value="doc" />
              </div>
            </div>
            <div class="row g-0 justify-content-md-center mb-4">
              <div class="col-12 col-md-10">
                <NuxtLink class="link-info fs-5" to="/compositores">Ver nuestro catálogo de compositores
                </NuxtLink>
              </div>
            </div>
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 col-lg-8 text-center">
                <img class="img-fluid" :src="doc.image">
                <br>
                <NuxtLink class="fs-6" :to="doc.linkArticuloImagen" target="_blank">{{doc.titleImage}}</NuxtLink>
              </div>
            </div>
          </ContentDoc>
        </section>
      </div>
    </div>
    <div class="row g-0 pt-5">
      <div class="col-12">
        <section>
          <ContentDoc path="/indexfiles/album" v-slot="{doc}">
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 text-justify">
                <ContentRenderer :value="doc" />
              </div>
            </div>
            <div class="row g-0 justify-content-md-center mb-4">
              <div class="col-12 col-md-10">
                <NuxtLink class="link-info fs-5" to="/albumes">Ver nuestro catálogo de álbumes</NuxtLink>
              </div>
            </div>
            <div class="row g-0 justify-content-md-center">
              <div class="col-12 col-md-10 col-lg-8 text-center">
                <img class="img-fluid" :src="doc.image">
                <br>
                <NuxtLink class="fs-6" :to="doc.linkArticuloImagen" target="_blank">{{doc.titleImage}}</NuxtLink>
              </div>
            </div>
          </ContentDoc>
        </section>
      </div>
    </div>
    <FooterView />
  </main>
</template>
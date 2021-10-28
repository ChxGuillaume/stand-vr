<template>
  <v-row justify-md="center" justify-lg="start">
    <v-col cols="12" class="mt-3 mb-10">
      <h1 class="text-h1 text-center">
        Stand VR
      </h1>
    </v-col>
    <v-col
      v-for="[index, game] of games.entries()"
      :key="game.name"
      class="d-flex justify-center"
      cols="12"
      lg="9"
      :offset-lg="index % 2 ? 3 : 0"
      xl="8"
      :offset-xl="index % 2 ? 3 : 1"
    >
      <v-card dark class="card_test flex-grow-1">
        <div
          class="d-flex flex-no-wrap justify-lg-space-between flex-column align-center"
          :class="{ 'flex-md-row-reverse': (index % 2), 'flex-md-row': !(index % 2) }"
        >
          <v-img
            class="rounded"
            width="385"
            max-width="min(100%, 385px)"
            max-height="180"
            :aspect-ratio="92 / 43"
            :src="game.image"
          />

          <div class="flex-grow-1">
            <v-card-title class="text-h5 text-center mx-auto" v-text="game.name" />

            <v-card-subtitle>
              <v-chip>
                {{ game.experience }}
              </v-chip>
              <v-chip class="ml-3">
                {{ game.sickness }}
              </v-chip>
            </v-card-subtitle>

            <div class="px-3" v-text="game.description" />

            <v-card-actions class="justify-center flex-column flex-md-row mt-3">
              <v-btn
                v-if="game.stand.n"
                class="ma-2 px-4"
                color="green"
                rounded
                large
              >
                Réserver (Stand N)
              </v-btn>

              <v-btn
                v-if="game.stand.t"
                class="ma-2 px-4"
                color="blue"
                rounded
                large
              >
                Réserver (Stand T)
              </v-btn>
            </v-card-actions>
          </div>
        </div>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data () {
    return {
      games: [
        {
          name: 'Job Simulator',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/448280/header.jpg?t=1632456268',
          description: 'Encore du boulot en weekend… Un jeu de simulation de travail humoristique au service des robots !',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Space Pirate Trainer',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/418650/header.jpg?t=1633233901',
          description: 'Un shot them’ up très immersif : tuez tous ces pirates de l’espace !',
          stand: { n: false, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'The Lab',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/450390/header.jpg?t=1632787478',
          description: 'Un court jeu d’initiation à la VR pour les plus novices !',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        }
      ]
    }
  }
}
</script>

<style scoped>
@media only screen and (max-width: 960px) {
  .card_test {
    width: 100%;
    max-width: 385px;
  }
}
</style>

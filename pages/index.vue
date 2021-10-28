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
            class="rounded ma-3"
            width="449"
            max-width="min(100%, 449px)"
            max-height="210"
            :aspect-ratio="92 / 43"
            :src="game.image"
          />

          <div class="flex-grow-1">
            <v-card-title class="text-h5 text-center mx-auto mb-3" v-text="game.name" />

            <v-card-subtitle>
              <v-chip :color="game.experience|experienceColor" outlined>
                Type {{ game.experience|experienceName }}
              </v-chip>
              <v-chip :color="game.sickness|sicknessColor" outlined class="ml-3">
                <v-icon left>
                  {{ game.sickness|sicknessIcon }}
                </v-icon>
                Gerbe {{ game.sickness|sicknessName }}
              </v-chip>
            </v-card-subtitle>

            <div class="px-3" v-text="game.description" />

            <v-card-actions class="justify-center flex-column flex-md-row mt-3">
              <v-btn
                v-if="game.stand.n"
                class="ma-2 px-4"
                color="primary"
                rounded
                large
              >
                Stand Code N
              </v-btn>

              <v-btn
                v-if="game.stand.t"
                class="ma-2 px-4"
                color="primary"
                rounded
                large
              >
                Stand Code T
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
  filters: {
    experienceName (value) {
      switch (value) {
        case 'starter':
          return 'Découverte'
        case 'newbie':
          return 'Standard'
        case 'experimented':
          return 'Expérimenté'
        default:
          return value
      }
    },
    experienceColor (value) {
      switch (value) {
        case 'starter':
          return 'green'
        case 'newbie':
          return 'orange'
        case 'experimented':
          return 'red'
        default:
          return 'grey'
      }
    },
    sicknessName (value) {
      switch (value) {
        case 'low':
          return 'Faible'
        case 'medium':
          return 'Moyenne'
        case 'high':
          return 'Élevé'
        case 'help':
          return 'Send Help'
        default:
          return value
      }
    },
    sicknessColor (value) {
      switch (value) {
        case 'low':
          return 'green'
        case 'medium':
          return 'orange'
        case 'high':
          return 'red'
        case 'help':
          return 'black'
        default:
          return value
      }
    },
    sicknessIcon (value) {
      switch (value) {
        case 'low':
          return 'mdi-emoticon'
        case 'medium':
          return 'mdi-emoticon-neutral'
        case 'high':
          return 'mdi-emoticon-dead'
        case 'help':
          return 'mdi-emoticon-devil'
        default:
          return value
      }
    }
  },
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
        },
        {
          name: 'Aperture Hand Lab',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/868020/header.jpg?t=1633960446',
          description: '',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Moss',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/846470/header.jpg?t=1623173225',
          description: '',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Beat Saber',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'Ragnarock',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'SuperHot',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'medium'
        },
        {
          name: 'The Room VR',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'Counter Fight',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'Zero Caliber',
          image: '',
          description: '',
          stand: { n: true, t: true },
          experience: 'newbie',
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

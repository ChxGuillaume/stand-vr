<template>
  <v-container>
    <v-row justify-md="center" justify-lg="start">
      <v-col cols="12" class="mt-3 text-center">
        <h1 class="text-h1">
          Stand VR
        </h1>
        <v-img
          :src="require('assets/valveindex.png')"
          alt="Index Headset"
          width="250"
          class="mx-auto my-5"
        />
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
              max-width="min(100% - 24px, 449px)"
              max-height="210"
              :aspect-ratio="92 / 43"
              :src="game.image"
            />

            <div class="flex-grow-1">
              <v-card-title class="text-h5 text-center mx-auto mb-3" v-text="game.name" />

              <v-card-subtitle>
                <v-chip :color="game.experience|experienceColor" outlined>
                  <v-icon left>
                    {{ game.experience|experienceIcon }}
                  </v-icon>
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
                  target="_blank"
                  href="https://nekotiki.fr/stand-n/"
                >
                  Stand Code N
                </v-btn>

                <v-btn
                  v-if="game.stand.t"
                  class="ma-2 px-4"
                  color="primary"
                  rounded
                  large
                  target="_blank"
                  href="https://nekotiki.fr/stand-t/"
                >
                  Stand Code T
                </v-btn>
              </v-card-actions>
            </div>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
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
    experienceIcon (value) {
      switch (value) {
        case 'starter':
          return 'mdi-new-box'
        case 'newbie':
          return 'mdi-google-controller'
        case 'experimented':
          return 'mdi-emoticon-cool'
        default:
          return value
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
          return 'grey darken-2'
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
          description: 'Votre but est d\'empêcher l\'invasion de votre château à l\'aide d\'un arc et de flèches !',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Aperture Hand Lab',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/868020/header.jpg?t=1633960446',
          description: 'Un court jeu d’initiation à la VR pour les plus novices !',
          stand: { n: true, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Moss',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/846470/header.jpg?t=1623173225',
          description: 'Jeu de plateau, le but est de faire progresser une petite sourie, Moss, en résolvant des énigmes et libérant des passages pour atteindre ses objectifs !',
          stand: { n: false, t: true },
          experience: 'starter',
          sickness: 'low'
        },
        {
          name: 'Beat Saber',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/620980/header.jpg?t=1635336215',
          description: 'Let\'s dance, Let’s break, Score those cubes !',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'Ragnarock',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/1345820/header.jpg?t=1635421189',
          description: 'Ragnarock, c’est Beat Saber mais pour les vrais Vikings !!',
          stand: { n: true, t: false },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'The Room VR',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/1104380/header.jpg?t=1634217668',
          description: 'A Dark Mater : Un jeu d’énigme en VR, incarnez la peau d’un enquêteur pour percer les mystères des différents niveaux !',
          stand: { n: false, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'Counter Fight',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/593210/header.jpg?t=1620317549',
          description: 'Samurai Edition : Vous avez toujours rêvé de travailler dans un restaurant Japonais ? Révisez vos recettes ! Itadakimasu !',
          stand: { n: false, t: true },
          experience: 'newbie',
          sickness: 'low'
        },
        {
          name: 'SuperHot',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/617830/header.jpg?t=1635043058',
          description: 'Aidez-vous du temps pour venir à bout de vos ennemis. Chaque geste compte ! Ne vous faites pas avoir !',
          stand: { n: true, t: true },
          experience: 'newbie',
          sickness: 'medium'
        },
        {
          name: 'Zero Caliber',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/877200/header.jpg?t=1633726434',
          description: 'Zero Caliber ce sont des missions avec des Guns pew pew, il faut tuer les pas gentils et allez au bout de la mission.',
          stand: { n: true, t: false },
          experience: 'newbie',
          sickness: 'medium'
        },
        {
          name: 'Propagation VR',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/1363430/header.jpg?t=1635211399',
          description: 'Un jeu de tir statique entouré de zombies… Attention aux âmes sensibles !',
          stand: { n: false, t: true },
          experience: 'experimented',
          sickness: 'low'
        },
        {
          name: 'Half Life Alyx',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/546560/header.jpg?t=1634491270',
          description: 'Gordon Freeman ?',
          stand: { n: false, t: true },
          experience: 'experimented',
          sickness: 'medium'
        },
        {
          name: 'VRChat',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/438100/header.jpg?t=1635454479',
          description: 'Alors, VRChat c\'est cool mais bon, plein de trucs a faire je sais pas quoi vous faire faire, t\'as quand meme envie ? :D',
          stand: { n: true, t: false },
          experience: 'experimented',
          sickness: 'medium'
        },
        {
          name: 'Blade & Sorcery',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/629730/header.jpg?t=1635255837',
          description: 'Coupez vos ennemis dans une arène en mode Sandbox, testez différentes armes, ou même, facultés magiques, pour les plus expérimentés !',
          stand: { n: false, t: true },
          experience: 'experimented',
          sickness: 'high'
        },
        {
          name: 'Project Cars 2',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/378860/header.jpg?t=1610244943',
          description: 'Prenez place sur la grille de départ à bord d’un bolide survolté ! (Volant et pédales mis à disposition)',
          stand: { n: false, t: true },
          experience: 'experimented',
          sickness: 'high'
        },
        {
          name: 'BoneWorks',
          image: 'https://cdn.cloudflare.steamstatic.com/steam/apps/823500/header.jpg?t=1633971106',
          description: 'Le bon jeu de la gerbe, globalement BoneWorks c’est de la simulation de physique, on peut prendre des objets, des armes et tuer des mobs giga chelou...',
          stand: { n: true, t: false },
          experience: 'experimented',
          sickness: 'help'
        }
      ]
    }
  },
  head: {
    title: 'Stand VR'
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

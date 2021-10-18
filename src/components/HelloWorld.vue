<template>
<v-container>
  <v-card fluid>
  <v-row>
    <v-sparkline
      :fill="fill"
      :gradient="selectedGradient"
      :line-width="width"
      :padding="padding"
      :smooth="radius || false"
      :value="value"
      auto-draw
    ></v-sparkline>
  </v-row>
    <v-divider></v-divider>

    <v-row>
      <v-col
        cols="12"
        md="6"
      >
        <v-row
          class="fill-height"
          align="center"
        >
          <v-item-group
            v-model="selectedGradient"
            mandatory
          >
          <v-divider></v-divider>
            <v-row>
              <v-space></v-space>
              <v-item
                v-for="(gradient, i) in gradients"
                :key="i"
                v-slot="{ active, toggle }"
                :value="gradient"
              >
              
                <v-card
                  :style="{
                    background: gradient.length > 1
                      ? `linear-gradient(0deg, ${gradient})`
                      : gradient[0],
                    border: '2px solid',
                    borderColor: active ? '#222' : 'white'
                  }"
                  width="30"
                  height="30"
                  class="mr-2"
                  @click.native="toggle"
                ></v-card>
              </v-item>
            </v-row>
          </v-item-group>
        </v-row>
      </v-col>

      <v-col cols="6">
        <v-row
          class="fill-height"
          align="center"
        >
          <v-switch
            v-model="fill"
            label="Filled"
          ></v-switch>
        </v-row>
      </v-col>
    </v-row>
  </v-card>
  <v-card>
    <v-tabs
    fixed-tabs
    background-color="dark-blue"
    color="blue"
    text
    dark
  >
    <v-tab>
      Automation
    </v-tab>
    <v-tab>
      campaign
    </v-tab>
    <v-tab>
      Segments
    </v-tab>
  </v-tabs>
  </v-card>
  <v-card
    class="mx-auto"
  >

  <v-list two-line>
      <v-list-item-group
        v-model="selected"
        active-class="blue--text"
        multiple
      >
        <template v-for="(item, index) in items">
          <v-list-item :key="item.title">
            <template v-slot:default="{ active }">
              <v-button>>
              <v-icon>
                mdi-cart
              </v-icon>
              </v-button>
              <v-list-item-content>
                <v-list-item-title v-text="item.title"></v-list-item-title>
                <v-list-item-subtitle
                  class="text--primary"
                  v-text="item.headline"
                ></v-list-item-subtitle>

                <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-list-item-action-text v-text="item.action"
                color='blue'
                text></v-list-item-action-text>

                <v-icon
                  v-if="!active"
                  color="grey lighten-1"
                >
                  mdi-star-outline
                </v-icon>

                <v-icon
                  v-else
                  color="yellow darken-3"
                >
                  mdi-star
                </v-icon>
              </v-list-item-action>
            </template>
          </v-list-item>

          <v-divider
            v-if="index < items.length - 1"
            :key="index"
          ></v-divider>
        </template>
      </v-list-item-group>
    </v-list>
  </v-card>
  </v-container>
</template>

<script>
  const gradients = [
    ['blue', 'blue', 'black'],
    ['red', 'red', 'black']
  ]
  export default {
    name: 'HelloWorld',
    data: () => ({
      fill: true,
      selectedGradient: gradients[4],
      gradients,
      padding: 10,
      radius: 10,
      value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
      width: 1,
      selected: [2],
      items: [
        {
          action: '$ 5,321',
          headline: 'Abandoned card 7 days',
          subtitle: `4024 sents | 124 clicks`,
          title: 'Ali Connors',
        },
        {
          action: '$ 5,321',
          headline: 'Abandoned card 15 mins',
          subtitle: `4024 sents | 124 clicks`,
          title: 'me, Scrott, Jennifer',
        },
        {
          action: '$ 5,321',
          headline: 'Abandoned card 15 mins',
          subtitle: '4024 sents | 124 clicks',
          title: 'Sandra Adams',
        }
      ]
    })
  }
</script>

<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <div id="signup" class="signup">
    <div class="narrow-wrapper">
      <div class="welcome box-unit">
        Welcome!
      </div>

      <div class="spacer">-</div>

      <div class="intro box-unit">
        What do you think about?
      </div>

      <div class="outro box-unit">
        Tip: You can add your own, <br>
        custom HashTags in the profile tab later.
      </div>

      <div class="spacer">-</div>

      <div class="hobbies box-unit">
        <div v-for="item in hobbies" class="hash-item" v-bind:class="{ 'active': item.state }" v-on:click="item.state=!item.state"><i class="fa fa-hashtag fa-fw hashtag"></i> <span class="text">{{item.tag}}</span></div>
      </div>

      <div class="spacer">-</div>

      <div class="done full-button box-unit" v-on:click="signup()">
        Done <i class="fa fa-check fa-fw"></i>
      </div>
    </div>
  </div>
</template>

<script>
  import WebSocket from '../obj/WebSocket'
  console.log(WebSocket.dummy)

  export default {
    data () {
      return {
        hobbies: [{state: false, tag: 'Gaming'}, {state: false, tag: 'Movies'}, {state: false, tag: 'Fishing'}, {state: false, tag: 'Gardening'}, {state: false, tag: 'Walking'}, {state: false, tag: 'Exercise'}, {state: false, tag: 'ListeningToMusic'}, {state: false, tag: 'Hunting'}, {state: false, tag: 'TeamSports'}, {state: false, tag: 'Shopping'}, {state: false, tag: 'Traveling'}, {state: false, tag: 'Sleeping'}, {state: false, tag: 'Socializing'}, {state: false, tag: 'VideoGames'}, {state: false, tag: 'Sewing'}, {state: false, tag: 'Golf'}, {state: false, tag: 'Relaxing'}, {state: false, tag: 'Crafts'}, {state: false, tag: 'WatchingSports'}, {state: false, tag: 'Bicycling'}, {state: false, tag: 'PlayingCards'}, {state: false, tag: 'Hiking'}, {state: false, tag: 'Cooking'}, {state: false, tag: 'EatingOut'}, {state: false, tag: 'Swimming'}, {state: false, tag: 'Camping'}, {state: false, tag: 'Skiing'}, {state: false, tag: 'Writing'}, {state: false, tag: 'Boating'}, {state: false, tag: 'Motorcycling'}, {state: false, tag: 'AnimalCare'}, {state: false, tag: 'Bowling'}, {state: false, tag: 'Painting'}, {state: false, tag: 'Running'}, {state: false, tag: 'Dancing'}, {state: false, tag: 'HorsebackRiding'}, {state: false, tag: 'Tennis'}, {state: false, tag: 'Billiards'}, {state: false, tag: 'VolunteerWork'}],
        msg: 'FirstLogin page.'
      }
    },
    methods: {
      signup: function () {
        var x = []
        var h = this.hobbies
        var keys = Object.keys(h)
        keys.forEach(function (e, i) {
          if (h[e].state) {
            x.push(h[e].tag)
          }
        })
        WebSocket.sendObj({m: 'signup', v: x})
        WebSocket.shortObj({m: 'signup', v: x})
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
  @import "../../sass/variables";
  @import "../../sass/mixins";

  #signup {
    background-color: $base;
    color: $base-alt;
    position: absolute;
    bottom: 0;
    right: 0;
    left: 0;
    top: 0;
    z-index: 10080;
    overflow: auto;
    text-align: center;
    padding: 0.5em;

    .box-unit {
    }

    .spacer {
      padding: 1em;
      text-align: center;
      visibility: hidden;
    }

    .welcome {
      font-size: 3.5em;
      margin-top: 1em;
    }

    .intro {
      font-size: 1.25em;
      font-weight: bold;
    }

    .hobbies {


      .hash-item{
        padding: 0.4em 1em;
        background-color: $base;
        color: $base-alt-soft;
        border: 0.1em solid $base-alt-soft;
        margin: 0.3em;
        display: inline-block;
        cursor: pointer;

        @include noselect;

        &:hover {
          color: lighten($base-alt-soft, 20%);
        }
        &.active {
          color: $accent-alt;
          border-color: $accent-alt;
          background-color: $accent;
        }
      }

      .text, .hashtag{
        font-size: 1.2em;
        line-height: inherit;
        pointer-events: none;
      }

      .hashtag {
        opacity: 0.5;
      }
    }

    .outro {
      margin-top: 1em;
    }

    .done {
      margin-bottom: 0.25em;

      @include noselect;
    }

  }
</style>

<template>
  <v-card class="content">
    <v-card-title>Content {{ state }} {{ name }}</v-card-title>
    <v-card-text>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Vero soluta
      temporibus nobis, eum modi tempore tempora delectus iusto nostrum minima
      dicta odit, magni magnam totam veniam veritatis sequi pariatur eveniet
      repudiandae velit minus rerum autem ab. Quasi dicta eos explicabo
      molestiae quis veritatis, possimus officia modi cum iste, quae veniam
      consectetur fugiat itaque dolorem quod tempora reiciendis! Deserunt
      debitis, numquam amet commodi quo obcaecati perspiciatis iste, pariatur
      odio consequuntur repudiandae nobis harum ducimus, voluptates at corporis.
      Quidem mollitia animi aperiam repellendus. Facere, cupiditate. Labore sed
      iste odio quisquam, exercitationem veniam quos. Asperiores laboriosam,
      iste enim velit doloribus vitae eligendi vero mollitia molestiae?
      Veritatis quia ipsa dignissimos voluptatum exercitationem at! Repellendus,
      assumenda praesentium! Commodi doloremque dignissimos reprehenderit amet
      ipsam quos culpa eveniet dicta? Quaerat, sunt sapiente sequi magnam totam
      consectetur. Odio a explicabo soluta adipisci tempora aperiam officiis
      sunt dignissimos quasi, excepturi facilis, totam omnis vel voluptatum
      voluptas pariatur accusantium minima voluptate fugit perferendis rem illo.
      Ut nisi placeat ipsam consequatur nobis aliquam et corrupti unde totam,
      error adipisci eligendi fugiat laborum. Aperiam nobis fugit ipsum odit eum
      tempore illo exercitationem id consequuntur praesentium nihil dignissimos
      quod officiis harum nam pariatur repellendus eos aspernatur ipsa
      consectetur laborum, voluptatibus dicta excepturi! Ipsa, ut repudiandae
      reiciendis a maxime necessitatibus odit inventore aspernatur quaerat
      fugit? Voluptatem, laudantium minus non accusantium praesentium a facere
      dolorem corporis ipsam aperiam! In, pariatur et, tenetur modi quos ut ad
      praesentium asperiores aspernatur voluptatibus earum ratione delectus sunt
      itaque voluptas consequatur eveniet magnam, odit rerum cum suscipit neque.
      Ut harum atque enim ad pariatur repellendus soluta veritatis, nostrum
      libero impedit corrupti architecto, officia eos omnis molestias magnam
      cumque vel blanditiis. Nisi, nihil maiores eius soluta corrupti omnis
      laboriosam tempora, molestiae, inventore autem provident repellat
      exercitationem cum itaque commodi rem praesentium et eveniet similique
      consectetur magni! Molestias quaerat eaque provident?
    </v-card-text>
  </v-card>
</template>

<script>
import axios from "axios";
export default {
  props: {
    state: Number,
  },
  data() {
    return {
      name: "",
    };
  },

  mounted() {
    axios
      .get("https://pokeapi.co/api/v2/pokemon/pikachu")
      .then((response) => (this.name = response.data.name));
  },
};
</script>

<style scoped>
.content {
  width: 100%;
  margin-left: 20px;
  padding: 24px;
  border: 1px solid rgba(0, 0, 0, 0.1);
}
</style>

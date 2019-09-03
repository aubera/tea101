<template>
  <div class="detail">
    <div class="nav">
      <h1>Tea 101</h1>
      <button @click="$router.push('/feedback')">
        <h2>Add opinion</h2>
      </button>
    </div>
    <div class="body">
      <SideNav :teas="teas" />
      <Description :tea="teas[selectedTeaId].description" />
    </div>
    <Opinion :user="opinions[selectedUserId]" />
    <!-- <ul>
      <li v-for="item in opinions">{{ item.name }}</li>
    </ul> -->
  </div>
</template>

<script>
import { eventBus } from "../main";
import SideNav from "@/components/SideNav.vue";
import Opinion from "@/components/Opinion.vue";
import Description from "@/components/Description.vue";

export default {
  name: "detail",
  components: {
    SideNav,
    Description,
    Opinion
  },
  data() {
    return {
      componentKey: 0,
      opinions: [
        {
          name: "Wang Shu",
          opinion:
            "What is today known as white tea may have come into creation in the last two centuries; scholars and tea merchants generally disagree as to when the first production of white tea (as it is understood in China today) began. White tea may have first appeared in English publication in 1876, where it was categorized as a black tea, because the leaves are not steamed first as in the making of green tea in order to denature intrinsic oxidative enzymes."
        },
        {
          name: "Yu Zhen",
          opinion:
            "Whether you are new to white tea or just looking for something unique and adventurous to satiate your palate, we have a wonderful selection of teas and blends to try."
        }
      ],
      teas: [
        {
          name: "Tea",
          description:
            "Understanding the “Art of Tea” in its entirety is an age old question that we are still continuously exploring today. With brand new tea knowledge and discoveries unveiling themselves each day, the journey into the world of tea is an exciting and limitless adventure with room for us all to explore, connect and interact. Being an engaged crew of tea educators,we have been fortunate enough to receive many wonderful insights on tea from its history to its preparation, all the while diving deeper into the various varietals that stem from the miraculously versatile camellia sinensis plant.While we can’ t begin to know everything about tea, we hope that we can help guide you with our extensive knowledge of what we do know about tea in this section. We know the importance of building a dynamic learning environment where you have all the tools you need to create your own personal tea journey.In addition to this, we know it is equally important to have a community forum where you have a voice to collaborate and share your ideas about tea and all its wonder.We look forward to your visits and your feedback as we share and discover the many facets of tea together. What is Tea ? (cont.) There is a separate category for herbal blends and fruit infusions, which are more properly characterized as tisanes.A tisane refers to a caffeine - free blend consisting of herbs, botanicals and / or fruits prepared like a tea, but technically not a tea.If the drink does not have tea leaves from Camellia Sinensis, it is not a tea.It is most likely a tisane.Therefore, it would be an oxymoron to call something an herbal tea because it can only be one or the other."
        },
        {
          name: "White Tea",
          description:
            "For many years it was believed that white tea was discovered during the Song Dynasty (920-1269), however, even earlier references to white tea have been traced as far back as the Tang Dynasty (618-907). At that time in history, white tea preparation was a very different experience than it is today: early harvest white tea leaves appeared solely in compressed cakes and broken pieces were steeped in earthenware kettles. Although white tea was popularized and widely revered in the Song Dynasty (960-1269), it was relatively unknown to the rest of the world until very recently. Only royals were allowed to consume white tea and it is rumored that it could only be served as a “tribute” to the emperor by virgins with white gloves as a symbol of honor and respect. One emperor, Hui Zong, became so enamored by white tea that it literally cost him most of his empire. During this time, ceremonial methods of preparing white tea were very similar to the traditional Japanese tea ceremony for matcha; typically in powder form and whisked in wide ceramic bowls. It wasn’t until the Ming Dynasty (1368-1644), that the Ming court ruled that only loose leaf white tea could be served as a tribute to the emperor, thus changing our understanding of white tea processing and its preparation forever."
        },
        {
          name: "Green Tea",
          description:
            "Green tea, also known as unoxidized tea, is made solely from the leaves of the camellia sinensis plant. The leaves are plucked, slightly withered, then immediately cooked to preserve the green quality and prevent oxidization. As a result of these methods, green teas have a much higher concentration of chlorophyll, polyphenols and antioxidants than other tea types. The growing conditions for green tea can be broken down between two different types: sun grown and shade grown. The leaves are generally harvested three times a year with the first flush producing the highest quality leaves. The heating process differs greatly depending on the region and the tea maker’s techniques. Some of the mainstream methods of manufacturing green tea include: Pan Firing - Chinese green teas are often pan or wok roasted to neutralize the natural enzymes then dried, which generally results in a pale green color such as our Dragonwell. Steaming – In general, most Japanese green teas are quickly deep steamed resulting in a bright green infusion."
        },
        {
          name: "Pu-erh Tea",
          description:
            "Pu-erh tea, known as “black tea” in the Far East part of the world, originates from the Yunnan province of China and is named after the market town in which it was first developed. Pu-erh tea is post-fermented, which means that the tea leaves go through a microbial fermentation process after they have been dried and rolled, causing the leaves to darken and change in flavor. This process allows the teas to not only improve with age like a fine wine, but many pu-erhs are able to retain their freshness for up to fifty years! Pu-erh teas can be found in compressed brick form or in loose leaf form and can be made from both green and black tea leaves. Puerh tea is made from a larger leaf strain of camellia sinensis called Dayeh, which are ancient trees with mature leaves that are said to be between 500 and 1000 years old. These trees are usually grown in temperate regions and although they can be harvested year-round, the opportune time to harvest is in mid-spring. Various conditions and environmental factors can impact the flavor profile of pu-erh, resulting in a rich experience for the tea drinker's palate of this bold tea that can be smooth, fruity, peaty, grassy, musky, herbal and earthy."
        },
        {
          name: "Oolong Tea",
          description:
            "Oolong (Wu-lung) tea originates from China and is actually transliterated from two words meaning “black” and “dragon” in English. Besides its inherent meaning, the two words describe the shape of the oolong leaves in their novel state. Oolong tea goes through a unique semi-oxidization process that ranges from 1% - 99%. Shortly after picking, the leaves are withered and semi-oxidized in the sun then shade dried. After this they are basket-tossed to break down the cells on the surface of the leaves and wok fired, which halts the oxidization process. Heating methods include masterfully hand roasting the tea leaves in multiple steps which generally take place throughout the night. Oolongs are often processed over charcoal or wood which gives a unique flavor to the various finishing styles. Finally, the leaves are curled or rolled into crispy shapes that resemble tiny black dragons, hence the descriptive name. Because oolong tea leaves are more mature, they are harvested later in the spring than green or white teas – usually from late April to early May."
        },
        {
          name: "Black Tea",
          description:
            "Black tea, also known as “red tea” in China for its rich, reddish infusion, is unique in that it is comprised from two different forms of the camellia sinensis plant: camellia sinensis sinensis and camellia sinensis assamica. Camellia Sinensis Sinensis yields shorter leaves and is primarily used in China and other neighboring East Asian countries. Camellia Sinensis Assamica has larger leaves and is used in parts of India and Sri Lanka. Dry black tea leaves are 100% oxidized, leaving them with a blackened color, thus earning its namesake. While the method in which it is produced varies from region to region, the process always involves withering, rolling, oxidization and drying. There are two primary methods of processing the leaves before they are graded: Orthodox Method – This is the most common method of processing black teas. With this method, more care is put into the tea leaves. After the leaves are picked, they are allowed to wither in the warm air for up to 18 hours to reduce their water content until they are soft and pliable. The leaves are then rolled in a special machine that gently presses and twists the leaves in order to break the cells to begin the oxidization process. This process can take several rounds, depending on the grade of leaf being cut. After the leaves are cut, they are once again exposed to the air in a climate controlled environment so that they can continue to oxidize, altering the level of polyphenols in the leaf. This is the point where the flavor of the leaf begins to develop. Once the leaves reach the appropriate oxidization level, they are then fed into a machine to dry, which halts the oxidization process. CTC (Cut, Tear, Curl) Method – This method was developed around the teabag boom of the 1950’s to facilitate the production of smaller cut tea leaves and a quicker processing time. While the production begins and ends in the same fashion with withering and drying, the rolling process is skipped in this method and the leaves are instead minced and broken apart in a rotorvane machine."
        }
      ],
      selectedTeaId: 0,
      selectedUserId: 0
    };
  },
  methods: {
    setRandomOpinionId() {
      this.selectedUserId = Math.round(
        Math.random() * (this.opinions.length - 1)
      );
    }
  },
  created() {
    eventBus.$on("userOpinion", data => {
      console.log(this.opinions.length);
      this.opinions.push(data);
      console.log(this.opinions.length);
      this.$forceUpdate();
      console.log(this.opinions.length);
      for (let i = 0; i < this.opinions.length; i++) {
        console.log(this.opinions[i].name);
      }
    });
    eventBus.$on("selectedTeaIndex", tea => {
      this.selectedTeaId = tea;
    });
    this.setRandomOpinionId();
  }
};
</script>

<style scoped lang="sass">
.detail
  display: flex
  flex-direction: column
  margin: auto
  width: 70vw

  .nav
    display: flex
    justify-content: space-between
    align-items: center

    h1
      float: left
      font-size: 3rem

    button
      height: 50px
      border-radius: 3px

  .body
    display: flex
    justify-content: space-between
</style>

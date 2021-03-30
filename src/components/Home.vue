<template>
  <div>
    <div class="home">
      <ul>
        <li>
          <a
            v-on:click="userChoose"
            ref="youtube"
            v-for="website in websiteNames"
            :key="website.id"
            :id="website.id"
            :name="website.name"
          >
            {{ website.name }}
          </a>
        </li>
      </ul>
      <div class="search_box">
        <form
          id="form"
          v-for="websitelink in websiteLinks"
          :key="websitelink.link"
          :action="websitelink.wikipediaLink"
          method="GET"
        >
          <input
            type="text"
            name="q"
            value=""
            id="input_box"
            v-model="message"
            placeholder="Search"
            autocomplete="off"
          />
        </form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Home",
  data() {
    return {
      message: "",
      websiteNames: [
        { name: "Youtube", id: 1 },
        { name: "Google ", id: 2 },
        { name: "DuckDuckGo", id: 3 },
        { name: "Wikipedia", id: 4 }
      ],
      websiteLinks: [
        {
          googleLink: `https://www.google.com/search${this.message}`,
          youtubeLink: `https://www.youtube.com/results?search_query${this.message}`,
          duckDuckGoLink: "",
          wikipediaLink:
            "https://en.wikipedia.org/wiki/Special:Search?search=hello"
        }
      ]
    };
  },
  methods: {
    userChoose: function() {
      // get websiteName from user
      const websiteName = event.target.getAttribute("name");
      console.log(websiteName);
    }
  }
};
</script>
<style scoped>
.home {
  font-family: "Dela Gothic One", cursive;
}
.home a {
  color: #45545c;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 2.3rem;
  cursor: pointer;
}
a:active {
  color: white;
}

.home li {
  display: flex;
  list-style-type: none;
  align-items: center;
  justify-content: center;
}
.search_box {
  height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
#input_box {
  height: 90%;
  width: 100%;
  font-size: 9rem;
  background-color: transparent;
  border: none;
  color: white;
  text-align: center;
}
input::placeholder {
  text-align: center;
}
</style>

<script>
import axios from "axios"; // Used to make HTTP requests

export default {
  name: "user-search",

  data() {
    return {
      hasSearched: false,
      formInput: "",
      user: "", // Placeholder while I configure backend
      followers: 0, // Placeholder while I configure backend
      twitchChannel: `https://www.twitch.tv/${this.user}`,
    };
  },

  methods: {
    // Function to handle form submission
    handleSubmit(event) {
      event.preventDefault();

      // Validates entry to make sure it isn't empty
      if (this.formInput === "" || this.formInput[0] === "_") {
        alert("Invalid entry...");
      } else {
        this.formInput = "";

        // Displays Twitch name and followers after a valid entry is submitted
        if (!this.hasSearched) {
          this.hasSearched = true;
        }
        // Gets username from form entry
        let username = event.target.name.value;

        // Makes an API call to the ExpressJS server
        axios.get(`/users/${username}`).then((res) => {
          this.user = res.data.user;
          this.followers = res.data.followers;
        });
      }
    },
  },
};

</script>

<template>
  <section>
    <form id="user-search" @submit="handleSubmit">
      <div>
        <input
          type="text"
          name="name"
          :value="formInput"
          @change="
            (e) => {
              formInput = e.target.value;
            }
          "
          placeholder="Enter your favorite Twitch channel..."
          autoComplete="off"
          pattern="^[a-zA-Z0-9_]{4,25}$"
        />
      </div>
      <button type="submit" class="submit w-button">Submit</button>
      <hr />
      <div class="results" v-if="hasSearched">
        <p class="channel">
          Twitch channel:
          <a :href="twitchChannel" target="_blank" rel="noreferrer noopener">
            {{ user }}
          </a>
        </p>
        <p class="followers">
          Follower count: <span>{{ followers.toLocaleString() }}</span>
        </p>
      </div>
    </form>
  </section>
</template>

<style>
a {
  text-decoration: none;
  color: rgb(255, 111, 89);
}

#user-search {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 50px 250px 50px 250px;
}

input,
.results {
  height: 48px;
  display: inline-block;
  border: 2px solid rgb(35, 58, 140);
  border-radius: 6px;
  box-sizing: border-box;
  color: rgb(232, 230, 227);
  background-color: transparent;
}

input[type="text"] {
  width: 420px;
  padding-left: 20px;
}

hr {
  flex-basis: 100%;
  height: 0;
  margin: 0;
  border: 0;
}

.submit {
  font-family: Inter, sans-serif;
  margin-left: 7px;
  font-size: 16px;
  height: 48px;
  padding-right: 24px;
  padding-left: 24px;
  -webkit-box-pack: center;
  -webkit-box-align: center;
  border: 2px solid rgb(35, 58, 140);
  border-radius: 6px;
  font-weight: 600;
  background-color: transparent;
  transition: background-color 0.5s, color 0.5s;
}

.submit:hover {
  background-color: rgb(35, 58, 140);
}

.w-button {
  color: rgb(232, 230, 227);
  text-decoration-color: initial;
  padding: 9px 15px;
  line-height: inherit;
  text-decoration: none;
  cursor: pointer;
}

.results {
  display: flex;
  justify-content: space-evenly;
  margin-top: 14px;
  font-size: 16px;
  padding: 10px 24px;
  width: auto;
}

.channel {
  margin-right: 15px;
}

.followers {
  margin-left: 15px;
}

.results span {
  color: rgb(78, 137, 211);
}

@media only screen and (min-width: 1025px) and (max-width: 1200px) {
  input {
    width: 400px;
  }

  .results {
    font-size: 15px;
    padding: 10px 20px;
  }

  #user-search {
    margin: 50px 200px 50px 200px;
  }
}

@media only screen and (min-width: 769px) and (max-width: 1024px) {
  input {
    width: 375px;
  }

  .results {
    font-size: 14px;
    padding: 11px 15px;
  }

  #user-search {
    margin: 50px 120px 50px 120px;
  }
}

@media only screen and (min-width: 631px) and (max-width: 768px) {
  input {
    width: 285px;
  }

  .results {
    width: 400px;
    font-size: 14px;
    padding-top: 2px;
    padding-right: 0px;
    padding-left: 42px;
  }

  #user-search {
    margin: 30px;
    margin-top: 50px 120px 50px 120px;
  }
}

@media only screen and (min-width: 571px) and (max-width: 630px) {
  input {
    width: 220px;
  }

  .results {
    width: 400px;
    font-size: 13px;
    padding-top: 2px;
    padding-right: 0px;
    padding-left: 10px;
  }

  #user-search {
    margin: 30px;
    margin-top: 50px 120px 50px 120px;
  }
}

@media only screen and (min-width: 521px) and (max-width: 570px) {
  input {
    width: 180px;
  }

  .results {
    width: 400px;
    font-size: 11px;
    padding-top: 12px;
    padding-right: 0px;
    padding-left: 5px;
  }

  #user-search {
    margin: 30px;
    margin-top: 50px 120px 50px 120px;
  }
}

@media only screen and (min-width: 481px) and (max-width: 520px) {
  input {
    width: 138px;
  }

  .results {
    width: 400px;
    font-size: 9.5px;
    padding-top: 6px;
    padding-right: 0px;
    padding-left: 5px;
  }

  #user-search {
    margin: 30px;
    margin-top: 50px 120px 50px 120px;
  }
}

@media only screen and (min-width: 407px) and (max-width: 480px) {
  input {
    width: 260px;
  }

  .results {
    width: 350px;
    font-size: 13px;
    padding: 0px 0px;
    padding-top: 3px;
    padding-left: 30px;
  }

  #user-search {
    margin: 14px;
    margin-top: 40px;
    margin-bottom: 25px;
  }
}

@media only screen and (min-width: 320px) and (max-width: 406px) {
  input {
    width: 170px;
  }

  .results {
    width: 275px;
    font-size: 11px;
    padding-right: 0px;
    padding-top: 7px;
    padding-left: 4px;
  }

  #user-search {
    margin: 14px;
    margin-top: 40px;
  }
}
</style>

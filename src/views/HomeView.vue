<template>
  <div class="container">
    <div class="header layout">
      <img
        width="70px"
        src="https://hcmut.edu.vn/img/nhanDienThuongHieu/01_logobachkhoasang.png"
      />
      <h1>SMART FARM PROJECT</h1>
    </div>
    <div class="sidebar layout" style="padding-top: 20px; overflow: hidden">
      <nav>
        <ul>
          <li>
            <a href="#">
              <img src="../assets/img/icon home.png" />
              Smart Farm
            </a>
          </li>
          <li>
            <a href="/history">
              <img src="../assets/img/history.png" />
              History
            </a>
          </li>
          <li>
            <a href="diagnose">
              <img src="../assets/img/disease-prevention.png" />
              Diagnose
            </a>
          </li>
          <li>
            <a href="#">
              <img src="../assets/img/weather.png" />
              Weather
            </a>
          </li>
          <li>
            <a href="#">
              <img src="../assets/img/help-web-button.png" />
              Help
            </a>
          </li>
        </ul>
      </nav>
    </div>
    <div class="value layout">
      <div class="value_col col_1">
        <h1>Temperature</h1>
        <h2>{{ state.dhtTempData }} &deg;C</h2>
        <img src="../assets/img/temperature.png" />
      </div>
      <div class="value_col col_2">
        <h1>Humidity</h1>
        <h2>{{ state.dhtHumData }} %</h2>
        <img src="../assets/img/humidity.png" />
      </div>
      <div class="value_col col_3">
        <h1>Light</h1>
        <h2>{{ state.lightData }} lux</h2>
        <img src="../assets/img/sensor.png" />
      </div>
      <div class="value_col col_4">
        <h1>Soil Moisture</h1>
        <h2>{{ state.soilData }} %</h2>
        <img src="../assets/img/soil-analysis.png" />
      </div>
    </div>
    <div class="status1 layout">
      <div class="status_col s_1">
        <div>
          <h1>Pump 1</h1>
          <h2 v-if="buttonStatus1" style="font-weight: 700; color: #00ac47;">Pump 1 is ON !!! </h2>
          <h2 v-if="!buttonStatus1" style="font-weight: 700; color: red;">Pump 1 is OFF !!!</h2>
        </div>
        <div class="stt">
          <img src="../assets/img/pump.png" />
          <div class="btn">
            <span class="text">OFF</span>
            <label class="switch">
              <input
                v-model="buttonStatus1"
                v-on:click="toggleButton1()"
                type="checkbox"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">ON</span>
          </div>
        </div>
      </div>
      <div class="status_col s_2">
        <div>
          <h1>Pump 2</h1>
          <h2 v-if="buttonStatus2" style="font-weight: 700; color: #00ac47;">Pump 2 is ON !!!</h2>
          <h2 v-if="!buttonStatus2" style="font-weight: 700; color: red;">Pump 2 is OFF !!!</h2>
        </div>
        <div class="stt">
          <img src="../assets/img/pump (1).png" style="width: 85px; margin-bottom: 5px"/>
          <div class="btn">
            <span class="text">OFF</span>
            <label class="switch">
              <input
                v-model="buttonStatus2"
                v-on:click="toggleButton2()"
                type="checkbox"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">ON</span>
          </div>
        </div>
      </div>
      <div class="status_col s_3">
        <div>
          <h1>Fan</h1>
          <h2 v-if="buttonStatus3" style="font-weight: 700; color:#00ac47;">Fan is ON !!!</h2>
          <h2 v-if="!buttonStatus3" style="font-weight: 700; color: red;">Fan is OFF !!!</h2>
        </div>
        <div class="stt">
          <img
            src="../assets/img/fan.png"
            style="width: 80px; margin-bottom: 5px; margin-top: 5px"
          />
          <div class="btn">
            <span class="text">OFF</span>
            <label class="switch">
              <input
                v-model="buttonStatus3"
                v-on:click="toggleButton3()"
                type="checkbox"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">ON</span>
          </div>
        </div>
      </div>
      <div class="status_col s_4">
        <div>
          <h1>Bulb</h1>
          <h2 v-if="buttonStatus6" style="font-weight: 700; color: #00ac47;">Bulb is ON !!! </h2>
          <h2 v-if="!buttonStatus6" style="font-weight: 700; color: red;">Bulb is OFF !!!</h2>
        </div>
        <div class="stt">
          <img  src="../assets/img/idea.png"
          style="width: 80px; margin-bottom: 5px; margin-top: 5px"  />
          <div class="btn">
            <span class="text">OFF</span>
            <label class="switch">
              <input
                v-model="buttonStatus6"
                v-on:click="toggleButton6()"
                type="checkbox"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">ON</span>
          </div>
        </div>
      </div>
      <div class="status_col s_6">
        <div>
          <h1>Shade Motor</h1>
          <h2 v-if="!buttonStatus4" style="font-weight: 700; color: red; padding-left: 15px;">Motor is OFF !!!</h2>
          <h2 v-if="buttonStatus4" style="font-weight: 700; color:#00ac47; padding-left: 15px;">Motor is ON !!!</h2>
          <!-- <h2 v-if="state.closeSwitch == 1" style="font-weight: 700; color: #2ecc71;">SunShade is CLOSE!</h2>
          <h2 v-if="state.openSwitch == 1 " style="font-weight: 700; color: #2ecc71;">SunShade is OPEN!</h2> -->
        </div>
        <div class="stt">
          <img
            src="../assets/img/timing-belt.png"
            style="width: 80px; margin-bottom: 5px; margin-top: 5px"
          />
          <div class="btn">
            <span class="text">OFF</span>
            <label class="switch">
              <input
                v-model="buttonStatus4"
                v-on:click="toggleButton4()"
                type="checkbox"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">ON</span>
          </div>
        </div>
      </div>
      <div class="status_col s_7">
        <div>
          <h1>Shade</h1>
          <h2 v-if="!buttonStatus7" style="font-weight: 700; color: blue;">Shade is OPEN !!!</h2>
          <h2 v-if="buttonStatus7" style="font-weight: 700; color:blue;">Shade is CLOSE !!!</h2>
        </div>
        <div class="stt">
          <img
            src="../assets/img/shade.png"
            style="width: 80px; margin-bottom: 5px; margin-top: 5px"
          />
          <div class="btn shade">
            <span class="text">OPEN</span>
            <label class="switch">
              <!-- <input
                v-model="buttonStatus7"
                v-on:click="toggleButton7()"
                type="checkbox"
              /> -->
              <input
                v-model="buttonStatus7"
                type="checkbox"
                :disabled="isDisabled"
              />
              <span class="slider round"></span>
            </label>
            <span class="text">CLOSE</span>
          </div>
        </div>
      </div>
      <!-- <div class="status_col s_plus">
        <img src="../assets/img/plus.png" />
        
      </div> -->
    </div>

    <div class="status2 layout">
      <h1>Settings</h1>
      <div class="btnauto">
        <span class="text1">Manual</span>
        <label class="switch">
          <input
            v-model="buttonStatus5"
            v-on:click="toggleButton5()"
            type="checkbox"
          />
          <span class="slider round"></span>
        </label>
        <span class="text1">Automatic</span>
      </div>
      <div style="width: 100%">
        <div class="form-set">
          <label class="form-label" for="temp-threshold">Temperature</label>
          <input
            class="form-input"
            v-model="tempThreshold"
            placeholder="C"
            type="number"
            id="temp-threshold"
            name="temp-threshold"
            :disabled="!buttonStatus5"
            required
          />
          <label class="form-label form-label--col2" for="humidity-threshold">Humidity</label>
          <input
            class="form-input"
            v-model="humThreshold"
            placeholder="%"
            type="number"
            id="humidity-threshold"
            name="humidity-threshold"
            :disabled="!buttonStatus5"
            required
          />
        </div>

        <div class="form-set">
          <label class="form-label" for="light-threshold">Light</label>
          <input
            class="form-input"
            v-model="lightThreshold"
            placeholder="lux"
            type="number"
            id="light-threshold"
            name="light-threshold"
            :disabled="!buttonStatus5"
            required
          />
          <label class="form-label form-label--col2" for="soil-moisture-threshold">Soil</label>
          <input
            class="form-input"
            v-model="soilThreshold"
            placeholder="%"
            type="number"
            id="soil-moisture-threshold"
            name="soil-moisture-threshold"
            :disabled="!buttonStatus5"
            required
          />
        </div>

        <div class="form-set">
          <label class="form-label" for="hour1-pump"
            >Thời gian tưới 1</label
          >
          <input
            class="form-input"
            v-model="hour1Pump"
            placeholder="hour"
            type="number"
            id="hour1-pump"
            name="hour1-pump"
            :disabled="!buttonStatus5"
            required
          />
          <label class="form-label form-label--col2" for="time1-pump"
            >Thời lượng tưới 1</label
          >
          <input
            class="form-input"
            v-model="time1Pump"
            placeholder="minutes"
            type="number"
            id="time1-pump"
            name="time1-pump"
            :disabled="!buttonStatus5"
            required
          />
        </div>

        <div class="form-set">
          <label class="form-label" for="hour2-pump"
            >Thời gian tưới 2</label
          >
          <input
            class="form-input"
            v-model="hour2Pump"
            placeholder="hour"
            type="number"
            id="hour2-pump"
            name="hour2-pump"
            :disabled="!buttonStatus5"
            required
          />
          <label class="form-label form-label--col2" for="time2-pump"
            >Thời lượng tưới 2</label
          >
          <input
            class="form-input"
            v-model="time2Pump"
            placeholder="minutes"
            type="number"
            id="time2-pump"
            name="time2-pump"
            :disabled="!buttonStatus5"
            required
          />
        </div>

        <div class="form-set">
          <label class="form-label" for="hour-motor"
            >Bắt đầu mở rèm</label
          >
          <input
            class="form-input"
            v-model="hourMotor"
            placeholder="hour"
            type="number"
            id="hour-motor"
            name="hour-motor"
            :disabled="!buttonStatus5"
            required
          />
          <label
            class="form-label form-label--col2"
            for="time-motor"
            >Thời lượng mở</label
          >
          <input
            class="form-input"
            v-model="timeMotor"
            placeholder="minutes"
            type="number"
            id="time-motor"
            name="time-motor"
            :disabled="!buttonStatus5"
            required
          />
        </div>

        <button type="submit" v-on:click="saveData()" id="save-btn" :disabled="!buttonStatus5">
          Save
        </button>
      </div>
    </div>

    <div class="footer layout">
      <h1>Design by: Nguyen Tien Phat - 1914598</h1>
    </div>
  </div>
</template>

<script scoped lang="ts">
import firebase from "../utl/firebase";
import { onMounted, reactive } from "vue";
import "firebase/database";
import {
  lm35Collection,
  dhtTempCollection,
  dhtHumCollection,
  lightCollection,
  soilCollection,
  pump1Status,
  pump2Status,
  fanStatus,
  motorStatus,
  bulbStatus,
  chenang,
  mode,
  settingThreshold,
  // openSwitch,
  // closeSwitch,
  hour1Pump,
  hour2Pump,
  hourMotor,
  humThreshold,
  lightThreshold,
  soilThreshold,
  tempThreshold,
  time1Pump,
  time2Pump,
  timeMotor,
} from "../utl/firebase";

export default {
  data: () => ({
    buttonStatus1: false,
    buttonStatus2: false,
    buttonStatus3: false,
    buttonStatus4: false,
    buttonStatus5: false,
    buttonStatus6: false,
    buttonStatus7: false,

    isDisabled: true,

    tempThreshold: "",
    humThreshold: "",
    lightThreshold: "",
    soilThreshold: "",

    hour1Pump: "",
    hour2Pump: "",
    time1Pump: "",
    time2Pump: "",
    hourMotor: "",
    timeMotor: "",
  }),

  mounted() {
    const buttonStatus11 = localStorage.getItem("buttonStatus1");
    if (buttonStatus11) {
      this.buttonStatus1 = JSON.parse(buttonStatus11);
    }
    pump1Status.on("value", (snapshot) => {
      this.buttonStatus1 = snapshot.val();
    });

    const buttonStatus22 = localStorage.getItem("buttonStatus2");
    if (buttonStatus22) {
      this.buttonStatus2 = JSON.parse(buttonStatus22);
    }
    pump2Status.on("value", (snapshot) => {
      this.buttonStatus2 = snapshot.val();
    });

    const buttonStatus33 = localStorage.getItem("buttonStatus3");
    if (buttonStatus33) {
      this.buttonStatus3 = JSON.parse(buttonStatus33);
    }
    fanStatus.on("value", (snapshot) => {
      this.buttonStatus3 = snapshot.val();
    });

    const buttonStatus44 = localStorage.getItem("buttonStatus4");
    if (buttonStatus44) {
      this.buttonStatus4 = JSON.parse(buttonStatus44);
    }
    motorStatus.on("value", (snapshot) => {
      this.buttonStatus4 = snapshot.val();
    });

    const buttonStatus55 = localStorage.getItem("buttonStatus5");
    if (buttonStatus55) {
      this.buttonStatus5 = JSON.parse(buttonStatus55);
    }
    mode.on("value", (snapshot) => {
      this.buttonStatus5 = snapshot.val();
    });

    const buttonStatus66 = localStorage.getItem("buttonStatus6");
    if (buttonStatus66) {
      this.buttonStatus6 = JSON.parse(buttonStatus66);
    }
    bulbStatus.on("value", (snapshot) => {
      this.buttonStatus6 = snapshot.val();
    });

    const buttonStatus77 = localStorage.getItem("buttonStatus7");
    if (buttonStatus77) {
      this.buttonStatus7 = JSON.parse(buttonStatus77);
    }
    chenang.on("value", (snapshot) => {
      this.buttonStatus7 = snapshot.val();
    });
    localStorage.setItem("buttonStatus7", JSON.stringify(this.buttonStatus7));

    hour1Pump.on("value", (snapshot) => {
      this.hour1Pump = snapshot.val();
    });
    hour2Pump.on("value", (snapshot) => {
      this.hour2Pump = snapshot.val();
    });
    hourMotor.on("value", (snapshot) => {
      this.hourMotor = snapshot.val();
    });
    time1Pump.on("value", (snapshot) => {
      this.time1Pump = snapshot.val();
    });
    time2Pump.on("value", (snapshot) => {
      this.time2Pump = snapshot.val();
    });
    timeMotor.on("value", (snapshot) => {
      this.timeMotor = snapshot.val();
    });
    humThreshold.on("value", (snapshot) => {
      this.humThreshold = snapshot.val();
    });
    lightThreshold.on("value", (snapshot) => {
      this.lightThreshold = snapshot.val();
    });
    soilThreshold.on("value", (snapshot) => {
      this.soilThreshold = snapshot.val();
    });
    tempThreshold.on("value", (snapshot) => {
      this.tempThreshold = snapshot.val();
    });
  },

  methods: {
    toggleButton1() {
      this.buttonStatus1 = !this.buttonStatus1;

      let obj1 = {
        buttonStatus1: this.buttonStatus1,
        timestap: new Date(),
      };

      firebase.firestore
        .collection("Pump1")
        .add(obj1)
        .catch((e) => {
          console.log(e);
        });

      pump1Status
        .set(this.buttonStatus1 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus1", JSON.stringify(this.buttonStatus1));
    },

    toggleButton2() {
      this.buttonStatus2 = !this.buttonStatus2;
      let obj2 = {
        buttonStatus2: this.buttonStatus2,
        timestap: new Date(),
      };
      firebase.firestore
        .collection("Pump2")
        .add(obj2)
        .catch((e) => {
          console.log(e);
        });

      pump2Status
        .set(this.buttonStatus2 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus2", JSON.stringify(this.buttonStatus2));
    },

    toggleButton3() {
      this.buttonStatus3 = !this.buttonStatus3;
      let obj3 = {
        buttonStatus3: this.buttonStatus3,
        timestap: new Date(),
      };
      firebase.firestore
        .collection("Fan")
        .add(obj3)
        .catch((e) => {
          console.log(e);
        });

      fanStatus
        .set(this.buttonStatus3 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus3", JSON.stringify(this.buttonStatus3));
    },

    toggleButton4() {
      this.buttonStatus4 = !this.buttonStatus4;
      let obj4 = {
        buttonStatus4: this.buttonStatus4,
        timestap: new Date(),
      };
      firebase.firestore
        .collection("Motor")
        .add(obj4)
        .catch((e) => {
          console.log(e);
        });

      motorStatus
        .set(this.buttonStatus4 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus4", JSON.stringify(this.buttonStatus4));
    },

    toggleButton5() {
      this.buttonStatus5 = !this.buttonStatus5;
      let obj5 = {
        buttonStatus5: this.buttonStatus5,
        timestap: new Date(),
      };
      firebase.firestore
        .collection("Mode")
        .add(obj5)
        .catch((e) => {
          console.log(e);
        });

      mode
        .set(this.buttonStatus5 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus5", JSON.stringify(this.buttonStatus5));
    },

    toggleButton6() {
      this.buttonStatus6 = !this.buttonStatus6;
      let obj6 = {
        buttonStatus6: this.buttonStatus6,
        timestap: new Date(),
      };
      firebase.firestore
        .collection("Bulb")
        .add(obj6)
        .catch((e) => {
          console.log(e);
        });

      bulbStatus
        .set(this.buttonStatus6 ? 1 : 0)
        .then(() => {})
        .catch((e) => {
          console.log(e);
        });

      localStorage.setItem("buttonStatus6", JSON.stringify(this.buttonStatus6));
    },

    saveData() {
      let obj7 = {
        tempThreshold: parseInt(this.tempThreshold),
        humThreshold: parseInt(this.humThreshold),
        lightThreshold: parseInt(this.lightThreshold),
        soilThreshold: parseInt(this.soilThreshold),
        hour1Pump: parseInt(this.hour1Pump),
        hour2Pump: parseInt(this.hour2Pump),
        time1Pump: parseInt(this.time1Pump),
        time2Pump: parseInt(this.time2Pump),
        hourMotor: parseInt(this.hourMotor),
        timeMotor: parseInt(this.timeMotor),
        timestamp: new Date(),
      };
      // if (
      //   !this.tempThreshold ||
      //   !this.humThreshold ||
      //   !this.lightThreshold ||
      //   !this.soilThreshold ||
      //   !this.hour1Pump ||
      //   !this.hour2Pump ||
      //   !this.time1Pump ||
      //   !this.time2Pump ||
      //   !this.hourMotor ||
      //   !this.timeMotor
      // ) {
      //   return;
      // }
      firebase.firestore
        .collection("setting threshold")
        .add(obj7)
        .catch((e) => {
          console.log(e);
        });

      // settingThreshold.set(obj7, (error) => {
      //   if (error) {
      //     console.log(error);
      //   } else {
      //     console.log("Data saved successfully.");
      //   }
      // });

      tempThreshold
        .set(parseInt(this.tempThreshold))
        .then(() => {})
        .catch((e) => {
        console.log(e);
      });
      humThreshold
        .set(parseInt(this.humThreshold))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      lightThreshold
        .set(parseInt(this.lightThreshold))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      soilThreshold
        .set(parseInt(this.soilThreshold))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      hour1Pump
        .set(parseInt(this.hour1Pump))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      hour2Pump
        .set(parseInt(this.hour2Pump))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      time1Pump
        .set(parseInt(this.time1Pump))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      time2Pump
        .set(parseInt(this.time2Pump))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      hourMotor
        .set(parseInt(this.hourMotor))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
      timeMotor
        .set(parseInt(this.timeMotor))
        .then(() => {})
        .catch((e) => {
          console.log(e);
      });
    },
  },

  setup() {
    const state = reactive({
      lm35Data: {},
      dhtTempData: {},
      dhtHumData: {},
      lightData: {},
      soilData: {},
      closeSwitch: {},
      openSwitch: {},
    });

    onMounted(async () => {

      let lm35DataSet = await lm35Collection.on("value", (snapshot) => {
        state.lm35Data = snapshot.val();
      });

      let dhtTempDataSet = await dhtTempCollection.on("value", (snapshot) => {
        state.dhtTempData = snapshot.val();
      });

      let dhtHumDataSet = await dhtHumCollection.on("value", (snapshot) => {
        state.dhtHumData = snapshot.val();
      });

      let lightDataSet = await lightCollection.on("value", (snapshot) => {
        state.lightData = snapshot.val();
      });

      let soilDataSet = await soilCollection.on("value", (snapshot) => {
        state.soilData = snapshot.val();
      });

      // let cswitchDataSet = await closeSwitch.on("value", (snapshot) => {
      //   state.closeSwitch = snapshot.val();
      // });

      // let owitchDataSet = await openSwitch.on("value", (snapshot) => {
      //   state.openSwitch = snapshot.val();
      // });

    });
    return { state };
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}

body {
  padding: 0px;
  font-family: Merriweather;
  font-size: 12px;
  color: #000;
}

.layout {
  background-color: rgb(168, 168, 235);
  /* border: 1px solid white; */
  min-height: 50px;
}

.container {
  display: grid;
  height: 100vh;
  grid-template-columns: 100px 1fr 1fr;
  grid-template-rows: 50px 1fr 1fr 50px;
  grid-template-areas:
    "header header header"
    "sidebar value value"
    "sidebar status1 status2"
    "sidebar footer footer";
}

/* ---------Thanh dau trang--------*/

.header {
  grid-area: header;
  color: blue;
  background-color: #70a1ff;
  display: flex;
}

.header h1 {
  font-size: 30px;
  margin: auto;
}

/*-----------------------------------*/

/*-------- Thanh menu ben trai------- */
.sidebar {
  grid-area: sidebar;
  background-color: #09006f;
}

.sidebar nav {
  height: 100%;
}

.sidebar nav ul {
  height: 100%;
  list-style-type: none;
  margin: 0px 0 20px 0;
}

.sidebar nav ul li {
  margin: 0px 0 40px 0;
}

.sidebar nav ul li a {
  display: flex;
  flex-direction: column;
  width: 100%;
  color: white;
  text-decoration: none;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.sidebar nav ul li a img {
  width: 50px;
  height: 50px;
}

.sidebar nav ul li a:hover {
  background-color: #2980b9;
  border-radius: 10px;
}

/*-----------------------------------*/

/*-------- hien thi gia tri------- */
.value {
  grid-area: value;
  display: flex;
  justify-content: space-evenly;
  background-color: white;
}

.value_col {
  display: flex;
  flex-direction: column;
  width: 22%;
  height: inherit;
  background-color: #e7d5ff;
  border-radius: 40px;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
  margin-bottom: 10px;
  font-size: 15px;
  /* box-shadow: 7px 7px 13px 4px rgba(102, 102, 102, 0.25); */
}

.col_1 {
  display: flex;
  padding-left: 10px;
  color: red;
}

.col_1 h2 {
  margin-top: 0px;
  font-size: 60px;
}

.col_1 img {
  width: 120px;
}

.col_2 {
  display: flex;
  padding-left: 10px;
  color: #1e90ff;
}

.col_2 h2 {
  margin-top: 0px;
  font-size: 60px;
}

.col_2 img {
  width: 120px;
}

.col_3 {
  display: flex;
  padding-left: 10px;
  color: orange;
}

.col_3 h2 {
  margin-top: 0px;
  font-size: 60px;
}

.col_3 img {
  width: 130px;
}

.col_4 {
  display: flex;
  padding-left: 10px;
  color: #2f3542;
}

.col_4 h2 {
  margin-top: 0px;
  font-size: 60px;
}

.col_4 img {
  width: 130px;
}

/*-----------------------------------*/

/*-------- hien thi trang thai------- */
.status1 {
  grid-area: status1;
  background-color: white;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr, 1fr);
  width: 900px;
  grid-gap: 20px;

  overflow: scroll;
}

.status_col {
  border-radius: 10px;
  color: #000;
  background-color: #e7d5ff;
  box-shadow: 7px 7px 13px 4px rgba(102, 102, 102, 0.25);
}

.status_col h1 {
  padding-left: 20px;
}

.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2196f3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

.btn {
  display: flex;
  /* justify-content: center; */
  align-items: center;
  justify-content: space-between;
  width: 150px;
}

.s_1 {
  margin: 10px 0px 0px 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.stt {
  width: 170px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.text {
  font-size: 20px;
  font-weight: 700;
  color: blue;
}

.shade {
  width: 190px;
  padding-right: 30px;
}

.s_1 img {
  width: 100px;
}

.s_2 {
  margin: 10px 50px 0px 0px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_2 img {
  width: 100px;
}

.s_3 {
  margin: 0px 0px 10px 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_3 img {
  width: 100px;
}

.s_4 {
  margin: 0px 50px 10px 0px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_4 img {
  width: 100px;
}

.s_6 {
  margin: 0px 0px 10px 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_6 img {
  width: 100px;
}

.s_7 {
  margin: 0px 50px 10px 0px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_7 img {
  width: 100px;
}

.s_plus {
  margin: 0px 0px 10px 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}

.s_plus img {
  width: 100px;
}

.status2 {
  grid-area: status2;
  display: flex;
  background-color: white;
  flex-direction: column;
  margin: auto;
}

.status2 {
  width: 450px;
  height: auto;
  background-color: #e7d5ff;
  color: blue;
  box-shadow: 7px 7px 13px 4px rgba(102, 102, 102, 0.25);
  border-radius: 40px;
  text-align: center;
  align-items: center;
  margin-top: 10px;
  margin-bottom: 10px;
}

.btnauto {
  display: flex;
  flex-direction: row;
  /* justify-content: center; */
  align-items: center;
  justify-content: space-between;
}

.text1 {
  font-size: 20px;
  font-weight: 400;
  color: #000;
  margin: 10px;
}

.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2196f3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

/* Rounded sliders */
.slider.round {
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

.form-set {
  padding: 4px 0;
  display: flex;
  color: #000;
  align-items: center;
}

.form-input {
  min-width: 50px;
  width: 70px;
  border: 2px;
  border-radius: 5px;
  height: 27px;
  padding-left: 10px;
}

.form-label {
  /* flex: 1; */
  width: 120px;
  padding-left: 10px;
  text-align: left;
}
.form-label--col2 {
  min-width: 130px;
}

#save-btn {
  border: 2px;
  border-radius: 5px;
  height: 30px;
  width: 50px;
  background-color: #ccc;
}

#save-btn:hover {
  background-color: #aaa;
}

.footer {
  grid-area: footer;
  font-size: 8px;
  text-align: center;
  justify-items: center;
  background-color: #70a1ff;
  color: white;
}

.footer h1 {
  margin-top: 15px;
}
</style>
<template>
  <div id="body-table">

    <div class="header">
      <div>
        <p>Шаповалова Дарья Сергеевна P3230</p>
        <p>Вариант 30017</p>
      </div>
    </div>

    <div class="body">
      <div class="choose-area">
        <div>
          <form id="coordinates-form">


            <div class="checkbox-area">
              <p>Выберите X:</p>
              <a id="forXError" style="font-size: 10px; font-style: oblique; color: #4C489D"></a>
              <div id="x-group">
                <div class="row">
                  <input class="ordinary-btn" id="-4" type="button" value="-4" name="x"
                         @click="rememberX(-4); paintButtons(-4)">
                  <input class="ordinary-btn" id="-3" type="button" value="-3" name="x"
                         @click="rememberX(-3); paintButtons(-3)">
                  <input class="ordinary-btn" id="-2" type="button" value="-2" name="x"
                         @click="rememberX(-2); paintButtons(-2)">
                </div>
                <div class="row">
                  <input class="ordinary-btn" id="-1" type="button" value="-1" name="x"
                         @click="rememberX(-1); paintButtons(-1)">
                  <input class="ordinary-btn" id="0" type="button" value="0" name="x"
                         @click="rememberX(0); paintButtons(0)">
                  <input class="ordinary-btn" id="1" type="button" value="1" name="x"
                         @click="rememberX(1); paintButtons(1)">
                </div>
                <div class="row">
                  <input class="ordinary-btn" id="2" type="button" value="2" name="x"
                         @click="rememberX(2); paintButtons(2)">
                  <input class="ordinary-btn" id="3" type="button" value="3" name="x"
                         @click="rememberX(3); paintButtons(3)">
                  <input class="ordinary-btn" id="4" type="button" value="4" name="x"
                         @click="rememberX(4); paintButtons(4)">
                </div>
              </div>

              <p>Выберите Y:</p>
              <div>
                <input id="yField" type="text" name="y" required="" placeholder="(-5;5)">
              </div>

              <p>Выберите R:</p>
              <div class="y-group">
                <div class="row">
                  <input class="ordinary-btn" type="button" value="-4" name="r" disabled>
                  <input class="ordinary-btn" type="button" value="-3" name="r" disabled>
                  <input class="ordinary-btn" type="button" value="-2" name="r" disabled>
                </div>
                <div class="row">
                  <input class="ordinary-btn" type="button" value="-1" name="r" disabled>
                  <input class="ordinary-btn" type="button" value="0" name="r" disabled>
                  <input class="ordinary-btn-R" id="r1" type="button" value="1" name="r"
                         @click="rememberR(1); paintButtonsR('r1')">
                </div>
                <div class="row">
                  <input class="ordinary-btn-R" id="r2" type="button" value="2" name="r"
                         @click="rememberR(2); paintButtonsR('r2')">
                  <input class="ordinary-btn-R" id="r3" type="button" value="3" name="r"
                         @click="rememberR(3); ; paintButtonsR('r3')">
                  <input class="ordinary-btn-selected-R" id="r4" type="button" value="4" name="r"
                         @click="rememberR(4); paintButtonsR('r4')">
                </div>
              </div>


            </div>
            <div class="buttons-area">
              <button id="function-btn" type="button" class="gradient-button" @click="validateInput()">
                Отправить
              </button>
            </div>
          </form>
        </div>

        <div id="graph-and-ttl">
          <svg id="graph_pic" height="300" width="300" xmlns="http://www.w3.org/2000/svg" @click="addPointFromGraph">

            <line stroke="black" x1="0" y1="150" x2="300" y2="150"/>
            <line stroke="black" x1="150" y1="0" x2="150" y2="300"/>
            <polygon fill="black" points="150,0 144,15 156,15" stroke="black"/>
            <polygon fill="black" points="300,150 285,156 285,144" stroke="black"/>

            <!-- Деления -->
            <line stroke="black" x1="200" y1="155" x2="200" y2="145"/>
            <line stroke="black" x1="250" y1="155" x2="250" y2="145"/>

            <line stroke="black" x1="50" y1="155" x2="50" y2="145"/>
            <line stroke="black" x1="100" y1="155" x2="100" y2="145"/>

            <line stroke="black" x1="145" y1="100" x2="155" y2="100"/>
            <line stroke="black" x1="145" y1="50" x2="155" y2="50"/>

            <line stroke="black" x1="145" y1="200" x2="155" y2="200"/>
            <line stroke="black" x1="145" y1="250" x2="155" y2="250"/>

            <!-- Подписи к делениям и осям -->
            <text fill="black" x="195" y="140">R/2</text>
            <text fill="black" x="250" y="140">R</text>

            <text fill="black" x="40" y="140">-R</text>
            <text fill="black" x="85" y="140">-R/2</text>

            <text fill="black" x="160" y="55">R</text>
            <text fill="black" x="160" y="105">R/2</text>

            <text fill="black" x="160" y="204">-R/2</text>
            <text fill="black" x="160" y="255">-R</text>

            <text fill="black" x="285" y="140">X</text>
            <text fill="black" x="160" y="15">Y</text>

            <!-- Квадрат(1-я четверть) -->
            <polygon id="rectangle" fill="#f3c3a6"
                     fill-opacity="0.2"
                     stroke="#f3c3a6"
                     points="150,150 150,100 250,100 250,150"/>

            <!-- Круг(2-я четверть) -->
            <path id="circle" fill="#f3c3a6"
                  fill-opacity="0.2"
                  stroke="#f3c3a6"
                  d="M 150,50 A100,100 0 0,0 50,150 L 150 150"/>

            <!-- Треугольник(3-я четверть) -->
            <polygon id="triangle" fill="#f3c3a6"
                     fill-opacity="0.2"
                     stroke="#f3c3a6"
                     points="150,150 150,200 100,150"/>
          </svg>

          <div id="ttl">
            <label for="ttlInput">Введите время (в формате чч:мм), по истечении которго запись
              должна удалиться.(По умолчанию значение равно 10 минут.)</label>
            <div>
              <input id="ttlInput" type="time" name="ttl" placeholder="" value="00:10" required="false">
            </div>
          </div>
        </div>

        <form id="hidden-form" style="display: none">
          <input type="text" id="pointX"/>
          <input type="text" id="pointY"/>
          <input type="text" id="pointR"/>
          <button type="submit" id="hidden-btn"></button>
        </form>

      </div>
    </div>

    <div>
      <div class="button-row">
        <button type="button" class="gradient-button" @click="deletePoints">Удалить все точки</button>
        <p></p>
      </div>
<br>
<div class="button-row"><br/> <p></p> <button type="button" class="gradient-button" @click="logout">Выход</button></div>

      <div class="table-area">

        <table id="main-table">
          <caption>ИСТОРИЯ ВЫПОЛНЕНИЙ</caption>
          <thead>
          <tr>
            <th class="col">X</th>
            <th class="col">Y</th>
            <th class="col">R</th>
            <th class="col">Результат</th>
            <th class="col">Текущее время</th>
            <th class="col">Срок жизни</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="point in points" v-bind:key="point.id">
            <td>{{ point.x }}</td>
            <td>{{ point.y }}</td>
            <td>{{ point.r }}</td>
            <td>{{ point.result }}</td>
            <td>{{ point.creationString }}</td>
            <td>{{ point.deathString }}</td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "main",
  data() {
    return {
      x: "",
      y: "",
      r: "4",
      xGraph: "",
      yGraph: "",
      points: new Array(0),
      ttl: "00:10"
    }
  },

  watch: {
    r() {
      let r = parseFloat(this.r);
      let circle = document.getElementById("circle");
      let rectangle = document.getElementById("rectangle");
      let triangle = document.getElementById("triangle");
      circle.setAttribute("d", `M 150 ${90 - 10 * r} A 100 100, 0, 0, 0, ${90 - 10 * r} 150 L 150 150 Z`);
      triangle.setAttribute("points", `${140 - 10 * r},150 150,150 150,${160 + 10 * r}`);
      rectangle.setAttribute("points", `${210 + 10 * r},150 150,150 150,${140 - 10 * r} ${210 + 10 * r},${140 - 10 * r} `);
      this.drawPoints();
    }
  },
  methods: {
    addPoints() {
      axios.post('http://localhost:8083/api/points/main', {
        x: document.getElementById('pointX').value,
        y: document.getElementById('yField').value.trim(),
        r: this.r,
        ttl: document.getElementById('ttlInput').value
      }, {
        headers: {"Authorization": "Bearer " + localStorage.getItem("jwt")}
      }).then(() => {
        this.getPoints();
        this.drawPoints();
      }, () => {
         this.$swal.fire({
          icon: "error",
          text: "Точку не удалось добавить",
          title: "Упс...",
           background: '#efe1d5',
           confirmButtonColor: '#8d7568',
        });
      }).catch(() => {
        this.$router.push({name: 'error-page-expired'})
      })
    },
    getPoints() {
      axios.get('http://localhost:8083/api/points/main', {
        headers: {"Authorization": "Bearer " + localStorage.getItem("jwt")}
      }).then((response) => {
        this.points = response.data;
        this.drawPoints();
      }).catch(() => {
        this.$router.push({name: 'error-page-expired'})
      })
    },
    deletePoints() {
      axios.delete('http://localhost:8083/api/points/main', {
        headers: {"Authorization": "Bearer " + localStorage.getItem("jwt")}
      }).then(() => {
        this.getPoints();
        this.$swal.fire({
          icon: "success",
          text: "Точки удалены!",
          title: "Вот и все!",
          background: '#efe1d5',
          confirmButtonColor: '#8d7568',
        });
      }, () => {
        this.$swal.fire({
          icon: "error",
          text: "Не получилось удалить точки",
          title: "Упс...",
          background: '#efe1d5',
          confirmButtonColor: '#8d7568',
        });
      }).catch(() => {
        this.$router.push({name: 'error-page-expired'})
      })
    },
    logout() {
      this.$swal({
        icon: "success",
        text: "До встречи!",
        title: "Вы успешно вышли",
        background: '#efe1d5',
        confirmButtonColor: '#8d7568',
      });
      this.$router.push({name: "auth-page"}, () => localStorage.clear());
    },

    drawPoints() {
      const svgSize = 300;
      let r = parseFloat(this.r);
      let svg = document.getElementById("graph_pic")
      let oldDots = document.querySelectorAll("circle");
      oldDots.forEach(oldDot => oldDot.parentNode.removeChild(oldDot));
      console.log(this.points.length);
      console.log(this.points)
      if (this.points.length !== 0) {
        this.points.forEach(point => {
          let newPoint = document.createElementNS("http://www.w3.org/2000/svg", "circle");
          newPoint.setAttribute("id", "target-dot");
          newPoint.setAttribute("r", "3.5");
          newPoint.setAttribute("cx", `${(point.x / 4) * 100 + svgSize / 2}`);
          newPoint.setAttribute("cy", `${svgSize / 2 - (point.y / 4) * 100}`);
          if (point.r === r) {
            newPoint.setAttribute("fill", point.result === "Попадание" ? "green" : "red");
            newPoint.setAttribute("r", "4.5");
          } else {
            newPoint.setAttribute("fill", "black");
            newPoint.setAttribute("opacity", "0.5");
          }
          svg.appendChild(newPoint);
        })
      }
    },
    addPointFromGraph() {
      let position = getMousePosition(document.getElementById("graph_pic"), event);
      this.xGraph = ((position.x - 150) / 100 * this.r).toFixed(2);
      this.yGraph = ((this.r * (150 - position.y)) / 100).toFixed(2);
      console.log(position.x, position.y);
      console.log(this.xGraph, this.yGraph);
      if (this.r >= 1 && this.r <= 4) {
        axios.post('http://localhost:8083/api/points/main', {
          x: this.xGraph,
          y: this.yGraph,
          r: this.r,
          ttl: document.getElementById('ttlInput').value
        }, {
          headers: {"Authorization": "Bearer " + localStorage.getItem("jwt")}
        }).then(() => {
          this.getPoints();
          this.drawPoints();
        }, () => {
          this.$swal.fire({
            icon: "error",
            text: "Не получилось добавить точку",
            title: "Упс..."
          });
        });
      } else {
        this.$swal.fire({
          icon: "error",
          text: "Вы выбрали неправильный радиус",
          title: "Упс..."
        });
      }

      function getMousePosition(element, event) {
        let rect = element.getBoundingClientRect();
        return {
          x: event.clientX - rect.left,
          y: event.clientY - rect.top
        };
      }
    },

    rememberX(value1) {
      document.getElementById('pointX').value = value1;
    }
    ,
    rememberR(value1) {
      document.getElementById('pointR').value = value1;
      this.r = value1;
    }
    ,
    validateInput() {
      let y;
      let yText = document.getElementById("yField");
      y = yText.value.trim();
      if (/^-?\d+\.?\d*$/.test(y)) {
        if (y >= 5 || y <= -5) yText.setCustomValidity("Число вне допустимого диапазона");
        else {
          yText.setCustomValidity("");
          if (document.getElementById('pointX').value !== '') {
            this.addPoints();
          } else {
            this.$swal.fire({
              icon: "error",
              text: "Вы не выбрали Х",
              title: "Упс...",
              background: '#efe1d5',
              confirmButtonColor: '#8d7568',
            });
          }
        }
      } else {
        this.$swal.fire({
          icon: "error",
          text: "Вы не выбрали Y",
          title: "Упс...",
          background: '#efe1d5',
          confirmButtonColor: '#8d7568',
        });
      }
    }
    ,


    paintButtons(id) {
      let selected = document.querySelectorAll(".ordinary-btn-selected");
      if (selected !== null) {
        document.querySelectorAll(".ordinary-btn-selected").forEach(function (i) {
              i.classList.toggle("ordinary-btn");
              i.classList.toggle("ordinary-btn-selected");
            }
        )
      }
      document.getElementById(id).classList.toggle("ordinary-btn"); //убрали обычный
      document.getElementById(id).classList.toggle("ordinary-btn-selected"); //добавили нажатый
    }
    ,
    paintButtonsR(id) {
      let selected = document.querySelectorAll(".ordinary-btn-selected-R");
      if (selected !== null) {
        document.querySelectorAll(".ordinary-btn-selected-R").forEach(function (i) {
              i.classList.toggle("ordinary-btn-R");
              i.classList.toggle("ordinary-btn-selected-R");
            }
        )
      }
      document.getElementById(id).classList.toggle("ordinary-btn-R"); //убрали обычный
      document.getElementById(id).classList.toggle("ordinary-btn-selected-R"); //добавили нажатый
    }
  }
  ,
  mounted() {
    this.getPoints();
    this.drawPoints();
  }
}
</script>

<style>
@import "../assets/header.css";
@import "../assets/body.css";
@import "../assets/adaptive.css";
@import "../assets/mountain.css";
</style>
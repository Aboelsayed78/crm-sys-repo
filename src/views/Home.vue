<template>
  <div class="home">
    <div class="dashboard">
      <!-- <h1><span>dash</span>board</h1> -->
      <div class="dash-cards">
        <div class="card active">
          <font-awesome-icon icon="ticket-alt" />
          <div class="card-contain">
            <span class="num-active">55</span>
            Active
          </div>
        </div>
        <div class="card finished">
          <font-awesome-icon icon="ticket-alt" />
          <div class="card-contain">
            <span class="num-finished">75</span>
            Finished
          </div>
        </div>
        <div class="card patients">
          <font-awesome-icon icon="user" />
          <div class="card-contain">
            <span class="num-patients">158</span>
            Patients
          </div>
        </div>
        <div class="card revenue">
          <font-awesome-icon icon="coins" />
          <div class="card-contain">
            <span class="num-revenue">5500 LE</span>
            This Month
          </div>
        </div>
      </div>
    </div>
    <hr />
    <div class="tickets-section">
      <div class="all-tickets">
        <div class="examines-tickets">
          <div class="h4s">
            <div class="left"><h4>left</h4></div>
            <div class="center"><h4>examines</h4></div>
            <div class="right"><h4>right</h4></div>
            <div class="clear"></div>
          </div>
          <div class="tickets-contain">
            <TicketComp
              onclick="document.getElementById('ticket-page').style.display='block'"
              v-for="patient in patients"
              :key="patient.id"
              :id="patient.id"
              :name="patient.name"
            />
          </div>
        </div>
        <div class="consults-tickets">
          <div class="h4s">
            <div class="left"><h4>left</h4></div>
            <div class="center"><h4>consults</h4></div>
            <div class="right"><h4>right</h4></div>
            <div class="clear"></div>
          </div>
          <div class="tickets-contain">
            <TicketComp
              onclick="document.getElementById('ticket-page').style.display='block'"
              v-for="patient in patients"
              :key="patient.id"
              :id="patient.id"
              :name="patient.name"
            />
          </div>
        </div>
        <div class="surgeries-tickets">
          <div class="h4s">
            <div class="left"><h4>left</h4></div>
            <div class="center"><h4>surgeries</h4></div>
            <div class="right"><h4>right</h4></div>
            <div class="clear"></div>
          </div>
          <div class="tickets-contain">
            <TicketComp
              onclick="document.getElementById('ticket-page').style.display='block'"
              v-for="patient in patients"
              :key="patient.id"
              :id="patient.id"
              :name="patient.name"
            />
          </div>
        </div>
        <div class="clear"></div>
      </div>
    </div>
    <hr />
    <div class="patients-section">
      <div class="all-patients">
        <div class="h4s">
          <div class="left"><h4>left</h4></div>
          <div class="center"><h4>new patients</h4></div>
          <div class="right"><h4>right</h4></div>
          <div class="clear"></div>
        </div>
        <div class="patients-contain">
          <div class="patient-panel-info">
            <span class="patient-img">img</span>
            <span class="patient">name</span>
            <span class="phone">phone</span>
            <span class="address">address</span>
            <span class="email">email</span>
          </div>
          <PatientComp
            v-for="patient in patients"
            :key="patient.id"
            :pic="patient.pic"
            :name="patient.name"
            :phone="patient.phone"
            :address="patient.address"
            :email="patient.email"
          />
        </div>
      </div>
    </div>
    <TicketPage
      v-for="patient in patients"
      :key="patient.id"
      :id="patient.id"
      :name="patient.name"
      :phone="patient.phone"
      :joined="patient.joined"
      :birth="patient.birth"
      :status="patient.status"
      :type="patient.type"
    />
  </div>
</template>

<script>
// @ is an alias to /src
// import $ from "jquery";
import TicketComp from "../components/TicketComp.vue";
import PatientComp from "../components/PatientComp.vue";
import TicketPage from "../components/TicketPage.vue";
import patientsData from "../json/Patients_Data.json";
export default {
  data: function () {
    return {
      patients: patientsData,
    };
  },
  name: "Home",
  props: {},
  components: {
    TicketComp,
    PatientComp,
    TicketPage,
  },
};
</script>

<style lang="scss">
@import "../assets/general.scss";
.home {
  padding: 15px;
  margin-top: 100px;
  .dashboard,
  .tickets-section,
  .patients-section,
  .doctors-section {
    h1 {
      text-align: left;
      margin: 20px 0;
      font-weight: bold;
      text-transform: capitalize;
      span {
        color: $main-color;
        border-bottom: 2px solid $main-color;
      }
    }
    .dash-cards {
      // Dashboard Cards
      display: flex;
      justify-content: space-between;
      padding: 5px 0;
      .card {
        // General Styling Of Cards
        float: left;
        width: 23.5%;
        height: 100px;
        padding-left: 5px;
        color: #999;
        border-radius: 3px;
        border: none;
        box-shadow: 2px 2px 4px 0px #ccc;
        transition: all 0.3s ease-in-out;
        font-size: 20px;
        font-weight: 400;
        position: relative;
        background-color: $main-color;
        &:hover {
          box-shadow: 1px 1px 4px 0px #999;
          padding: 3px 3px 3px 50px;
          color: #555;
          .card-contain {
            border-radius: 2px;
          }
        }
        .card-contain {
          background-color: #eee;
          padding: 10px;
          height: 100%;
        }
        span {
          display: block;
          font-weight: bold;
          font-size: 30px;
        }
        svg {
          position: absolute;
          top: 35%;
          left: 3%;
          color: #eee;
          font-size: 30px;
        }
        &.revenue {
          svg {
            left: 4%;
          }
        }
        &.patients {
          svg {
            left: 5%;
          }
        }
      }
    }
  }
  /////////////////////////////////////////////////////////////////////
  hr {
    height: 2px;
    width: 600px;
    margin: 50px auto;
    color: #999;
  }
  /////////////////////////////////////////////////////////////////////
  .tickets-section {
    // Tickets Style
    .all-tickets {
      .examines-tickets,
      .consults-tickets,
      .surgeries-tickets,
      .all-patients {
        // Urgent and Normal Tickets Style
        float: left;
        width: 32.3%;
        margin: 0 1.5% 15px 0;
        .h4s {
          overflow: hidden;
          .left,
          .right,
          .center {
            float: left;
            width: 32%;
            background-color: $main-color;
            h4 {
              border-radius: 0 0 10px 0;
              background-color: #fff;
              text-transform: capitalize;
              text-align: center;
              font-size: 20px;
              padding: 4px 15px;
              margin: 0px auto;
              color: transparent;
            }
          }
          .center {
            width: 36%;
            background-color: #fff;
            h4 {
              background-color: $main-color;
              border-radius: 25px 25px 0 0;
              color: #fff;
            }
          }
          .right {
            h4 {
              border-radius: 0 0 0 10px;
            }
          }
        }
        .tickets-contain {
          background-color: #fff;
          height: 200px;
          overflow: scroll;
          padding: 5px;
          border: 2px solid $main-color;
          border-radius: 3px;
          box-shadow: 1px 1px 5px 0px #999;
          .ticket {
            .ticket-panel {
              background-color: #eee;
              padding: 5px;
              margin-bottom: 5px;
              border-radius: 3px;
              cursor: pointer;
              &:hover {
                background-color: #ddd;
              }
              span {
                text-align: left;
                display: inline-block;
                line-height: 1.7;
                font-size: 18px;
                border-right-color: $main-color;
                &.id {
                  width: 20%;
                  text-align: center;
                  background-color: $main-color;
                  color: #fff;
                  margin-right: 15%;
                  border-radius: 3px;
                  border-right: none;
                }
                &.patient {
                  width: 65%;
                  margin-right: 0;
                  border-right: none;
                  text-transform: capitalize;
                }
                &.appoint {
                  width: 25%;
                  margin-right: 0;
                }
                &.status,
                &.type,
                &.appoint,
                &.phone {
                  display: none;
                }
              }
            }
          }
        }
      }
      .surgeries-tickets {
        // Normal Tickets Only
        margin-right: 0;
      }
    }
  }
  /////////////////////////////////////////////////////////////////////
  .patients-section {
    // patients Style
    .all-patients {
      .h4s {
        overflow: hidden;
        .left,
        .right,
        .center {
          float: left;
          width: 40%;
          background-color: $main-color;
          h4 {
            border-radius: 0 0 25px 0;
            background-color: #fff;
            text-transform: capitalize;
            text-align: center;
            padding: 8px 15px;
            margin: 0px auto;
            color: transparent;
          }
        }
        .center {
          width: 20%;
          background-color: #fff;
          h4 {
            background-color: $main-color;
            border-radius: 25px 25px 0 0;
            color: #fff;
          }
        }
        .right {
          h4 {
            border-radius: 0 0 0 25px;
          }
        }
      }
      .patients-contain {
        background-color: #fff;
        height: 350px;
        overflow: scroll;
        padding: 5px;
        border: 2px solid $main-color;
        border-radius: 3px;
        box-shadow: 1px 1px 5px 0px #999;
        .patient-panel,
        .patient-panel-info {
          background-color: #eee;
          padding: 5px;
          margin-bottom: 5px;
          border-radius: 3px;
          overflow: hidden;
          cursor: pointer;
          &:hover {
            background-color: #ddd;
          }
          span {
            text-align: center;
            float: left;
            font-size: 20px;
            text-transform: capitalize;
            line-height: 2.4;
            border-right-color: $main-color;
            &.patient-img {
              width: 8%;
              border-left: none;
              line-height: 2.4;
              padding: 0 1%;
              img {
                width: 100%;
                border-color: $main-color;
                border-radius: 50%;
              }
            }
            &.patient,
            &.phone {
              display: inline-block;
              width: 22%;
            }
            &.address {
              width: 18%;
            }
            &.email {
              width: 30%;
              padding: 0 1%;
              display: inline-block;
              border-right: none;
              text-transform: lowercase;
            }
            &.date,
            &.active,
            &.finish {
              display: none;
            }
          }
        }
        .patient-panel-info {
          background-color: #ddd;
          cursor: inherit;
          span {
            font-weight: bold;
            line-height: 2;
            border-right: 1px solid #999;
            &.patient-img {
              line-height: 2;
            }
          }
        }
      }
    }
  }
  .doctors-section {
    // patients Style
    .all-doctors {
      .h4s {
        overflow: hidden;
        .left,
        .right,
        .center {
          float: left;
          width: 40%;
          background-color: $main-color;
          h4 {
            border-radius: 0 0 25px 0;
            background-color: #fff;
            text-transform: capitalize;
            text-align: center;
            padding: 8px 15px;
            margin: 0px auto;
            color: transparent;
          }
        }
        .center {
          width: 20%;
          background-color: #fff;
          h4 {
            background-color: $main-color;
            border-radius: 25px 25px 0 0;
            color: #eee;
          }
        }
        .right {
          h4 {
            border-radius: 0 0 0 25px;
          }
        }
      }
      .doctors-contain {
        background-color: #fff;
        padding: 5px;
        border: 2px solid $main-color;
        border-radius: 5px;
        box-shadow: 1px 1px 5px 0px #999;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        .doctor {
          width: 25%;
          margin-bottom: 0;
          .doctor-panel {
            button {
              background-color: $main-color;
            }
          }
        }
      }
    }
  }
}
</style>

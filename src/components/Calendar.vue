<template>
  <article id="calendar">
    <header>
      <div class="current-date">
        <div class="current-day">
          Saturday
        </div>
        <div class="today">
          <div><div class="arrow-up"></div></div>
          <div><div class="arrow-up"></div></div>
          <div><div class="arrow-up"></div></div>
          <div>10</div>
          <div>August</div>
          <div>2019</div>
          <div><div class="arrow-down"></div></div>
          <div><div class="arrow-down"></div></div>
          <div><div class="arrow-down"></div></div>
        </div>
      </div>
    </header>
    <section>
      <div class="weekdays">
        <div class="weekday" v-for="(weekday, index) in weekdays" :key="index">
          {{ weekday }}
        </div>
      </div>
      <div class="date">
        <div class="day-hidden">29</div>
        <div class="day-hidden">30</div>
        <div class="day-hidden">31</div>
        <div class="day" v-for="(n, index) in 31" :key="index">
          {{ n }}
        </div>
        <div class="day-hidden" v-for="(n, index) in 8" :key="index">
          {{ n }}
        </div>
      </div>
    </section>
  </article>
</template>

<script>
  export default {
    data: function() {
      return {
        weekdays: ['Mo','Th','We','Th','Fr','Sa','Su'],
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css?family=Anton');

  @mixin calendar-layout($property) {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(50px, 1fr));
    grid-gap: 10px;
    padding: $property;

    div {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 30px;
      color: #fff;
      border-radius: 5px;
    }
  }

  @mixin arrow-style() {
    width: 0;
    height: 0;
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    cursor: pointer;
  }

  #calendar {
    width: 460px;
    height: 730px;
    background-color: #efefef;
    font-family: 'Anton';
    border-radius: 15px;
    overflow: hidden;
    background: url('../assets/calendar/8.png') center center;
    background-size: cover;

    header {
      display: flex;
      justify-content: center;
      align-items: top;
      height: 400px;
      padding: 20px 0 0;
      text-align: center;
      overflow: hidden;
      color: #efefef;
      text-shadow: 1px 1px 1px #222,
        1px -1px 1px #222,
        -1px 1px 1px #222,
        -1px -1px 1px #222;

      .current-date {
        width: 300px;
      }

      .arrow-up {
        @include arrow-style();
        border-bottom: 10px solid #fff;

        &:hover {
          border-bottom: 10px solid rgba(0,0,0,.4);
        }
      }

      .arrow-down {
        @include arrow-style();
        border-top: 10px solid #fff;

        &:hover {
          border-top: 10px solid rgba(0,0,0,.4);
        }
      }

      .today {
        display: grid;
        grid-template-columns: 40px auto 70px;
        grid-gap: 0;

        div {
          display: flex;
          justify-content: center;
        }
      }

      .current-day {
        font-size: 4rem;
      }

      .today {
        font-size: 2rem;
      }
    }

    .weekdays {
      @include calendar-layout(10px 20px 10px);
      background-color: rgba(0,0,0,.5);
      border-bottom: 1px solid #fff;

      div:nth-child(7n) {
        color: #D43541;
      }
    }

    .date {
      @include calendar-layout(10px 20px 20px);
      background-color: rgba(0,0,0,.7);

      .day {
        cursor: pointer;

        &:hover {
          background-color: #fff;
          color: #2A4C50;
        }

        &:nth-child(7n) {
          color: #D43541;

          &:hover {
            background-color: #fff;
            color: #D43541;
          }
        }
      }

      .day-hidden {
        opacity: .4;

        &:nth-child(7n) {
          color: #D43541;
        }
      }
    }
  }
</style>

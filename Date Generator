// ALAWAYS-REQUIRED
// VARIABLES
    const datesArray = [];
    const currentEverything = new Date();
    const currentDayOfTheMonth = new Date().getDate();
    const currentDayOfTheWeek = new Date().getDay();
    const days = [
      "Sunday",
      "Monday",
      "Tuesday",
      "Wednesday",
      "Thursday",
      "Friday",
      "Saturday",
    ];

// ALWAYS-REQUIRED
// FUNCTION | Transforms the string value(s) to numerical values (0-6 | JS day values)
// COMMENTS | Strings must be equal to the string values in days array
    function transformStringToNumber(array) {
      return array.map((string) => days.indexOf(string));
    }

// ARRAY-REQUIRED
// FUNCTION | Sorts the array from lowest number to highest number (0-6 | JS day values)
    async function sortArrayNumerically(array) {
      return array.sort(function (a, b) {
        return a - b;
      });
    }

// ARRAY-REQUIRED
// FUNCTION | Finds if the day values are before, current, or after the current day of the current week
    async function findDayOfCurrentWeekForEach(array) {
      let dateDifference = await array.map(
        (item) => item - currentDayOfTheWeek
      );
      let currentWeeksDates = [];
      for (let i = 0; i < dateDifference.length; i++) {
        let desiredDatesOfThisWeek = new Date().getDate();
        switch (true) {
          case array[i] === currentDayOfTheWeek:
            currentWeeksDates.push(desiredDatesOfThisWeek);
            break;
          case dateDifference[i] === currentDayOfTheWeek:
            desiredDatesOfThisWeek = currentDayOfTheMonth + dateDifference[i];
            currentWeeksDates.push(desiredDatesOfThisWeek);
            break;
          case dateDifference[i] < currentDayOfTheWeek:
            dateDifference[i] = dateDifference[i] * -1;
            desiredDatesOfThisWeek =
              currentDayOfTheMonth + 7 - dateDifference[i];
            currentWeeksDates.push(desiredDatesOfThisWeek);
            break;
          case dateDifference[i] > currentDayOfTheWeek:
            desiredDatesOfThisWeek = currentDayOfTheMonth + dateDifference[i];
            currentWeeksDates.push(desiredDatesOfThisWeek);
            break;
          default:
            console.log("No true case statement was found");
        }
      }
      await sortArrayNumerically(currentWeeksDates);
      return currentWeeksDates;
    }

// ARRAY-REQUIRED
// FUNCTION | Generates data and stores it in datesArray (12 values)
// COMMENTS | Change line 76 (i < x) for x amount of values
    async function findDesiredDaysWithMonths(availableDay) {
      const dayValues = await transformStringToNumber(availableDay);
      const desiredDayCurrentWeek = await findDayOfCurrentWeekForEach(
        dayValues
      );
      let id = 0;
      for (let i = 0; i < 12; i++) {
        let week = 7 * i;
        for (let i = 0; i < availableDay.length; i++) {
          let desiredDayFullDate = new Date(
            currentEverything.getFullYear(),
            currentEverything.getMonth(),
            currentEverything.getDate() -
              currentDayOfTheMonth +
              desiredDayCurrentWeek[i] +
              week
          );

          let desiredDayFullStringDate = desiredDayFullDate.toDateString();
          let month = desiredDayFullStringDate.slice(4, 7);
          let date = desiredDayFullStringDate.slice(8, 10);
          let day = desiredDayFullStringDate.slice(0, 3);
          datesArray.push({ id, month, date, day });
          id++;
        }
      }
    }

// ALTERNATIVE FUNCTIONS | Use these if generating data for only one day

// STRING-REQUIRED
// FUNCTION | Finds if the day value is before, current, or after the current day of the current week
    function findDesiredDayOfCurrentWeek(day) {
      let desiredDay = days.indexOf(day);
      let dateDifference = desiredDay - currentDayOfTheWeek;
      let desiredDatesOfThisWeek = currentDayOfTheMonth;
      if (desiredDay == currentDayOfTheWeek) {
        return desiredDatesOfThisWeek;
      } else if (dateDifference < currentDayOfTheWeek) {
        dateDifference = dateDifference * -1;
        desiredDatesOfThisWeek = currentDayOfTheMonth + 7 - dateDifference;
        return desiredDatesOfThisWeek;
      } else if (dateDifference > currentDayOfTheWeek) {
        desiredDatesOfThisWeek = currentDayOfTheMonth + dateDifference;
        return desiredDatesOfThisWeek;
      }
      return desiredDatesOfThisWeek;
    }

// STRING-REQUIRED
// FUNCTION | Generates data and stores it in datesArray (12 values)
// COMMENTS | Change line 123 (i < x) for x amount of values
    function findDesiredDaysWithMonths(day) {
      let currentDesiredDay = findDesiredDayOfCurrentWeek(day);
      let id = 1;
      for (let i = 0; i < 12; i++) {
        let week = 7 * i;
        let desiredDayFullDate = new Date(
          currentEverything.getFullYear(),
          currentEverything.getMonth(),
          currentEverything.getDate() -
            currentDayOfTheMonth +
            currentDesiredDay +
            week
        );
        let desiredDayFullStringDate = desiredDayFullDate.toDateString();
        let date = desiredDayFullStringDate.slice(8, 10);
        let month = desiredDayFullStringDate.slice(4, 7);
        datesArray.push({ id, month, date });
        id++;
      }
    }

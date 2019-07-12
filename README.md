# Javascript Problem Solving Notes #

A list about `Javascript` problem and its solution

## Problem (1) - await inside forEach 

You cant use `await` inside `forEach`.
because it will give you error :

>**SyntaxError: await is only valid in async function**

for example :

**WRONG:**

    async function getSchedule(_object, _date) {
      _object.forEach( function (elem) {
        var city_id = elem.id;
        var schedule_url = 'http://localhost/api/format/json/schedule/city/'+city_id+'/date/'+_date;    
        response = await request( schedule_url );  
        await timer(100);
        });
      }
    }

**CORRECT:**

    async function getSchedule(_object, _date) {
      for (var key in _object) {
        var city_id = _object[key].id;
        var schedule_url = 'http://localhost/api/format/json/schedule/city/'+city_id+'/date/'+_date;
        response = await request( schedule_url );
        await timer(100);
      }
    }



**Note: Because this is still few contents, i will not use index...

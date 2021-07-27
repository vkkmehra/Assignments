# Task 1

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

# Solution Code:
```
let num = 121;
function checkPalindrome(num) {
    let tempNo = num;
    let reverse = 0;

    if (num < 0) return false
    
    while (tempNo > 0) {
        if (tempNo < 10) reverse += tempNo;
        else reverse = (reverse + (tempNo % 10)) * 10
        tempNo = Math.floor(tempNo / 10)
    }

    if (reverse == num)
        return true
}

if (checkPalindrome(num)) console.log(num + " is a palindrome integer")
else console.log(num + " is not a palindrome integer")
```

# Task 2
You are given an array prices where prices[i] is the price of a given stock on the ith day.
Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).
Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

# Solution Code:
```
let price = [1, 2, 3, 1, 15, 6, 7]

function findMaxProfit() {
    // length of array means no. of days for which prices are available
    let totalDays = price.length;
    // console.log(totalDays)
    let totalProfit = 0;

    if (price.length < 2) {
        console.log("At least two values are required to peform buy and sell.")
        return;
    }

    // main loop to iterate through each day
    for (i = 0; i < totalDays; i++) {
        // find first smaller price as compared to next price in each iteration
        for (buyDay = i; buyDay < totalDays - 1;) {
            // if next day's price is lesser than current day price then move next as it is not smaller price then
            if (price[buyDay] >= price[buyDay + 1])
                buyDay++;
            else
                break;
        }

        // if first minimum price is on last day then no profit can be earned, exit loop
        if (buyDay == totalDays - 1)
            break;

        // post increment as next loop need to start from next day of first min price day to find sell price
        buy = buyDay++;
        // console.log("buy" + buy + " price" + price[buy]);
        // find last bigger price as compared to previous price
        for (sellDay = buyDay; sellDay < totalDays;) {
            // if previous day's price is lesser than current day price then move next as it is not a bigger price then
            if (price[sellDay] >= price[sellDay - 1])
                sellDay++;
            else
                break;
        }

        sell = sellDay - 1;
        //console.log("sell",sell);
        // console.log("sell" + sell + " price" + price[sell]);
        totalProfit += (price[sell] - price[buy])

        i = sellDay - 1;

    }
    console.log("Total Profit is : ", totalProfit)
}

findMaxProfit()
```

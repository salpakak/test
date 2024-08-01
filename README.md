module.exports = function reverse (n) {
    n = Math.abs(n);
    let str = n.toString();
    let result = '';
    for (let i = str.length - 1; i >= 0; i--) { 
        result += str[i];
    }
    return result;
}


module.exports = function toReadable (number) {
    let result = '';
    const numberWords = [
        "zero", "one", "two", "three", "four", "five", 
        "six", "seven", "eight", "nine", "ten", 
        "eleven", "twelve", "thirteen", "fourteen", 
        "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"
    ];
    const tensWords = [
        "", "", "twenty", "thirty", "forty", "fifty", 
        "sixty", "seventy", "eighty", "ninety"
    ];
    
    if (number === 0) {
        return 'zero';
    } else if (number < 20) {
        return numberWords[number];
    } else if (number < 100) {
        let tens = Math.floor(number / 10);
        let units = number % 10;
        result = tensWords[tens];
        if (units > 0) {
            result +=  ` ${numberWords[units]}`;
        }
        return result;
    } else if (number < 1000) {
        let hundreds = Math.floor(number / 100);
        let remainder = number % 100;
        result = `${numberWords[hundreds]} hundred`;
        if (remainder > 0) {
            result += ` ${toReadable(remainder)}`;
        }
        return result;
    }
}


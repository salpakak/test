module.exports = function towelSort (matrix) {
  let result = [];
  if (!Array.isArray(matrix) || matrix.length === 0) {
    return [];
  }
  matrix.forEach((element, index) => {
    if (Array.isArray(element)) {
      if (index % 2 === 0) {
        result = result.concat(element);
      } else {
        result = result.concat(element.reverse());
      }
    } else {
      result.push(element);
    }
  });
  return result;
}


function decode(expr) {
    let result = "";
    let segments = expr.match(/.{10}/g);
    for (let segment of segments) {
        if (segment === '**********') {
            outPut += ' ';
        } else {
            let morse = '';         
            for (let i = 0; i < segment.length; i += 2) {
                let pair = segment.slice(i, i + 2);
                if (pair === '10') {
                    morse += '.';
                } else if (pair === '11') {
                    morse += '-';
                }
            }  
            result += MORSE_TABLE[morse];
        }
    }

    return result;
}



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


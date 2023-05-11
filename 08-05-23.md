function permute(str) {
    let result = [];
    if (str.length === 0) {
      return [];
    } else if (str.length === 1) {
      return [str];
    }
    for (let i = 0; i < str.length; i++) {
      let chr = str[i];
      let remaining = str.slice(0, i) + str.slice(i + 1);
      let subPerms = permute(remaining);
      for (let j = 0; j < subPerms.length; j++) {
        result.push(chr + subPerms[j]);
      }
    }
    return result;
  }
  
  let input = "1867";
  let permutations = permute(input);
  let divisibleBy7 = [];
  for (let i = 0; i < permutations.length; i++) {
    if (parseInt(permutations[i]) % 7 === 0) {
      divisibleBy7.push(parseInt(permutations[i]));
    }
  }
  if (divisibleBy7.length === 0) {
    console.log("No permutations are divisible by 7");
  } else {
    let smallest = Math.min(...divisibleBy7);
    let largest = Math.max(...divisibleBy7);
    let average = (smallest + largest) / 2;
    console.log(`The smallest permutation divisible by 7 is ${smallest}`);
    console.log(`The largest permutation divisible by 7 is ${largest}`);
    console.log(`The average of the smallest and largest is ${average}`);
  }
  
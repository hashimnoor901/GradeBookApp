function getAverage(arr){
    let total = 0;
    for(let i of arr){
      total += i;
    }
    return total / arr.length;
}

function getGrade(score){
  if(score === 100) return "A+";
  if(score >= 90) return "A";
  if(score >= 80) return "B";
  if(score >= 70) return "C";
  if(score >= 60) return "D";
  return "F";
}

function hasPassingGrade(score){
  return getGrade(score) !== "F";
}

function studentMsg(scoreArr, stdScore){
  const stdAverage = getAverage(scoreArr);
  const stdGrade = getGrade(stdScore);
  const passOrFail = hasPassingGrade(stdScore);

  if(passOrFail){
    return `Class average: ${stdAverage}. Your grade: ${stdGrade}. You passed the course.`;
  } else {
    return `Class average: ${stdAverage}. Your grade: ${stdGrade}. You failed the course.`;
  }
}

document.getElementById("calculateBtn").addEventListener("click", function(){
  const classInput = document.getElementById("classScores").value;
  const studentScore = Number(document.getElementById("studentScore").value);

  const scoreArray = classInput
    .split(",")
    .map(score => Number(score.trim()));

  const message = studentMsg(scoreArray, studentScore);

  document.getElementById("result").textContent = message;
});
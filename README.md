<h1>Coding Training - Kata Boolean</h1>
<h2>Qui andremo a riportare gli esercizi elencati, con anche le duvute correzioni</h2>
<p>Membri del gruppo:</p>
<ul>
  <li>Gianmaria Fadda</li>
  <li>Riccardo Mauri</li>
  <li>Laura Oliveri</li>
  <li>Youssef Abdelmalak</li>
</ul>
<hr>
<h1>Primo esercizio</h1>
<h2>In breve: in base ad un determinato input, creare la frase di apertura della telecronaca del MotoGP.</h2>
<b>Codice Errato</b>
<hr>
<p>Sample Tests</p>
<hr>
<p>const { assert } = require('chai');
const name = 'Marc Marquez'

describe('Fixed Tests', () => {
  it('Racer is in the front row', () => {
    assert.strictEqual(
      gridPosition(name, 2),
      'Marc Marquez starts from the middle of the front row',
      'Incorrect answer for rider = Marc Marquez, position = 2'
    );
    assert.strictEqual(
      gridPosition(name, 3),
      'Marc Marquez starts from the bottom of the front row',
      'Incorrect answer for rider = Marc Marquez, position = 3'
    );
  });
  it('Racer is in pole', () => {
    assert.strictEqual(
      gridPosition(name, 1),
      'Marc Marquez starts from pole position',
      'Incorrect answer for rider = Marc Marquez, position = 1'
    );
  });
  it('Racer in various positions', () => {
    assert.strictEqual(
      gridPosition(name, 11),
      'Marc Marquez starts from the middle of the 4th row',
      'Incorrect answer for rider = Marc Marquez, position = 11'
    );
    assert.strictEqual(
      gridPosition(name, 13),
      'Marc Marquez starts from the top of the 5th row',
      'Incorrect answer for rider = Marc Marquez, position = 13'
    );
    assert.strictEqual(
      gridPosition(name, 9),
      'Marc Marquez starts from the bottom of the 3rd row'
    );
  });
});
</p>
<hr>
<img src="https://github.com/user-attachments/assets/9777256a-3345-4618-898d-22dc1b08a187" alt="Kata-1">
<hr>
<b>Codice Corretto</b>
<hr>
<p>const gridPosition = (name, position) => {
  const row = Math.ceil(position / 3);
  const col = position % 3 || 3;

  if (position === 1) 
    return ${name} starts from pole position;

  if (row === 1) {
    if (col === 1)
      return ${name} starts from the top of the front row;
    if (col === 2)
      return ${name} starts from the middle of the front row;
    if (col === 3)
      return ${name} starts from the bottom of the front row;
  }

  const positionInRow = col === 1 ? 'top' : col === 2 ? 'middle' : 'bottom';
  return ${name} starts from the ${positionInRow} of the ${row}${order(row)} row;
};

const order = (number) => {
  const lastNumber = number % 10;
  const lastTwoNumber = number % 100;

  if (lastNumber === 1) 
    return 'st';

  if (lastNumber === 2) 
    return 'nd';

  if (lastNumber === 3) 
    return 'rd';

  return 'th';
};</p>
<hr>
<img src="https://github.com/user-attachments/assets/977454a5-d7b8-4093-949a-48bf96b89d8f" alt="Kata-Solution-1">

<h1>Secondo esercizio</h1>
<h2>In breve: sapendo come cresce la popolazione di una città, calcolare quanti anni servono per arrivare ad un determinato valore</h2>
<b>Codice Errato</b>
<hr>
<p>Sample Tests</p>
<hr> 
<p>const Test = require('@codewars/test-compat');

describe("nbYear",function() {
it("Basic tests",function() {    
    Test.assertEquals(nbYear(1500, 5, 100, 5000), 15);
    Test.assertEquals(nbYear(1500000, 2.5, 10000, 2000000), 10);
    Test.assertEquals(nbYear(1500000, 0.25, 1000, 2000000), 94);
    Test.assertEquals(nbYear(1000, 2.0, 50, 1214), 4, "Did you maybe forgot to round down population at the end of each year?");
})})</p>
<hr>
<img src="https://github.com/user-attachments/assets/e70c8c1f-8445-496e-b8c9-ad415dce3193" alt="Kata-2">
<hr>

<b>Codice Corretto</b>
<hr>
<p>function nbYear(p0, percent, aug, p) {
  let year = 0;
    percent /= 100;
  while (p0 < p) {
    p0 += Math.floor(p0 * percent) + aug;
    year++;
  }
  return year;
}</p>
<hr>
<img src="https://github.com/user-attachments/assets/1e6ae653-60f7-4e2a-8e00-77f3d0042350" alt="Kata-2-Risolto">
<hr>
<h1>terzo esercizio</h1>
<h2>In breve: cercare un paio di occhiali nelle stringhe di un array!</h2>
<b>Codice Errato</b>
<hr>
<p>Sample Tests</p>
<hr>
<p>const chai = require("chai");
const assert = chai.assert;

const doTest = (arr, expected) => 
  it(`findGlasses(${JSON.stringify(arr)})`, () => assert.strictEqual(findGlasses(arr), expected))

//Fixed Tests
describe("Fixed Tests", () => {
  doTest(['phone', 'O-O', 'coins', 'keys'], 1)
  doTest(['OO', 'wallet', 'O##O', 'O----O'], 3)
  doTest(['O_O', 'O-O', 'OwO'], 1)
  doTest(['O--#--O', 'dustO---Odust', 'more dust'], 1)
  doTest(['floor', 'the floor again', 'pockets', 'bed', 'cabinet', 'the top of my head O-O'], 5)
  doTest(['OOOO----~OOO', '-------', 'OOOOOOO', 'OO-OO-OO-O'], 3)
});</p>
<hr>
<img src="https://github.com/user-attachments/assets/5694a87b-6cfd-42be-a681-43b8fcd4332e" alt="Kata-3">
<hr>
<b>Codice Corretto</b>
<hr>
<p>function findGlasses(arr) {
    for (let i = 0; i < arr.length; i++) {
        const item = arr[i];
        if (/O[-]+O/.test(item)) {
            return i;
        }
    }
}</p>
<img src="https://github.com/user-attachments/assets/f0217b0d-98b4-4e61-a700-2988158ccd76" alt="Kata-3-Risolto">
<hr>
<h1>Quarto Esercizio</h1>
<h2>In breve: calcolare i bonus di un gruppo di team in base a determinate regole.</h2>
<b>Codice Errato</b>
<hr>
<p>Sample Test</p>
<hr>
<p>const Test = require('@codewars/test-compat');

describe("Basic Tests", function(){ 
it("It should works for basic tests.", function(){

Test.assertEquals(minimumBonus([20,30,10,30,40,10,20,30,40,30]),20)

Test.assertEquals(minimumBonus([10,20,30]),6)

Test.assertEquals(minimumBonus([30,20,10]),6)

Test.assertEquals(minimumBonus([30,20,20,10]),6)

Test.assertEquals(minimumBonus([10,20,20,30]),6)

Test.assertEquals(minimumBonus([20,20,20,20]),4)

Test.assertEquals(minimumBonus([20,30,40,30,20,10]),13)

})})</p>
<hr>
<img src="https://github.com/user-attachments/assets/ed64abc9-c75f-4f32-ae8e-932e9d76670c" alt="Kata-4">
<hr>
<b>Codice Corretto</b>
<hr>
<p>
  function minimumBonus(scores) {
    let bonus = Array(scores.length).fill(1);

  for (let i = 1; i < scores.length; i++) {
        if (scores[i] > scores[i - 1]) {
            bonus[i] = bonus[i - 1] + 1;
        }
    }
    for (let i = scores.length - 2; i >= 0; i--) {
        if (scores[i] > scores[i + 1]) {
            bonus[i] = Math.max(bonus[i], bonus[i + 1] + 1);
        }
    }
    let sum = 0;
    for (let i = 0; i < bonus.length; i++) {
        sum += bonus[i];
    }
    return sum;
}
</p>
<img src="https://github.com/user-attachments/assets/0bed6390-1caa-413b-aff0-921e370a2475" alt="Kata-4-Risolto">

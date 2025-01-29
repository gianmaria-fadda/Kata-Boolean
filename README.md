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

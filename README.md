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

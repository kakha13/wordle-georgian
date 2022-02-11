<template>
  <section>
    <div class="instructions">
      <p>გამოიცანი <strong>დღის სიტყვა</strong> 6 ცდაში.</p>
      <p>
          აკრიფეთ სიტყვა და დააჭირეთ 'Enter'
      </p>
      <p>
          ყოველი ცდის შემდეგ გამოჩნდება ფერი, რომელიც გაჩვენებთ თუ რამდენად ახლოს ხართ დღის სიტყვასთან.
      </p>
      <div class="examples">
        <p><strong>მაგალითები</strong></p>
        <div class="example">
            <div class="row">
            <div class="tile correct">
                <div class="front">კ</div>
            </div>
            <div class="tile">
                <div class="front">ა</div>
            </div>
            <div class="tile">
                <div class="front">ხ</div>
            </div>
            <div class="tile">
                <div class="front">ა</div>
            </div>
            <div class="tile">
                <div class="front">ს</div>
            </div>
          </div>
          <p>
            ასო [კ] არის დღის სიტყვაში და სწორ პოზიციაზე.
          </p>
        </div>
        <div class="example">
          <div class="row">
            <div class="tile">
                <div class="front">ბ</div>
            </div>
            <div class="tile present">
                <div class="back">ა</div>
            </div>
            <div class="tile">
                <div class="front">რ</div>
            </div>
            <div class="tile">
                <div class="front">გ</div>
            </div>
            <div class="tile">
                <div class="front">ი</div>
            </div>
          </div>
       
          <p>ასო [ა] არის დღის სიტყვაში მაგრამ არასწორ პოზიციაზე.</p>
          
        </div>
        <div class="example">
          <div class="row">
            <div class="tile">
                <div class="front">ა</div>
            </div>
            <div class="tile">
                <div class="front">ე</div>
            </div>
            <div class="tile">
                <div class="front">რ</div>
            </div>
            <div class="tile absent">
                <div class="back">ი</div>
            </div>
            <div class="tile">
                <div class="front">ა</div>
            </div>
          </div>
          <p>
            ასო [ი] არ არის დღის სიტყვაში.
          </p>
        </div>
      </div>
      <p>
        <strong>დღის სიტყვა იცვლება 24 საათში ერთხელ</strong>
      </p>
      <strong><strong> </strong></strong>
    </div>
  </section>
</template>

<style scoped>
  .instructions {
    padding: 16px;
    padding-top: 0px;
    font-size: 15px;
    color: var(--color-tone-1)
  }

  .examples {
    border-bottom: 1px solid var(--color-tone-4);
    border-top: 1px solid var(--color-tone-4);
  }

  .example {
    margin-top: 24px;
    margin-bottom: 24px;
  }

  .example .correct { 
     border-color: var(--green);
  }
  .example .present { 
     border-color: var(--yellow);
  }

  .example .absent { 
     border-color: var(--color-tone-2);
  }
  .example .tile {
    margin-right: 3px;
    width: 40px;
    height: 40px;
    font-size: 20px;
  }

  .example p {
      font-size: 16px;
  }

  :host([page]) section {
    padding: 16px;
    padding-top: 0px;
  }

  </style>
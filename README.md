interface Ability {
  name: string;
  use(): void;
}
class FuriousStrike implements Ability {
  name = "Furious Strike";

  use(): void {
    console.log("Dealt 50 damage with a powerful strike!");
  }
}

class Heal implements Ability {
  name = "Heal";

  use(): void {
    console.log("Recovered 30 HP!");
  }
}

class ShadowMagic implements Ability {
  name = "Shadow Magic";

  use(): void {
    console.log("Cast dark magic, dealing damage and weakening the enemy!");
  }
}
class Hunter {
  name: string;
  level: number;
  abilities: Ability[] = [];

  constructor(name: string, level: number) {
    this.name = name;
    this.level = level;
  }

  equipAbility(ability: Ability): void {
    this.abilities.push(ability);
    console.log(`${this.name} equipped the ability: ${ability.name}`);
  }

  useAbility(index: number): void {
    if (index >= 0 && index < this.abilities.length) {
      const ability = this.abilities[index];
      console.log(`${this.name} used ${ability.name}:`);
      ability.use();
    } else {
      console.log("Invalid ability index.");
    }
  }

  showInfo(): void {
    console.log(`Hunter: ${this.name}`);
    console.log(`Level: ${this.level}`);
    console.log("Abilities:");
    this.abilities.forEach((ability, i) => {
      console.log(`  [${i}] ${ability.name}`);
    });
  }
}
function simulateCombat() {
  const jinWoo = new Hunter("Sung Jin-Woo", 50);

  const strike = new FuriousStrike();
  const heal = new Heal();
  const shadow = new ShadowMagic();

  jinWoo.equipAbility(strike);
  jinWoo.equipAbility(heal);
  jinWoo.equipAbility(shadow);

  console.log("\n--- Hunter Status ---");
  jinWoo.showInfo();

  console.log("\n--- Combat Begins! ---");
  jinWoo.useAbility(0); // Furious Strike
  jinWoo.useAbility(1); // Heal
  jinWoo.useAbility(2); // Shadow Magic
  console.log("--- Combat Ends! ---");
}

simulateCombat();


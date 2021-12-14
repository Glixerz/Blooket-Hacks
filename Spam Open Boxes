const capitalize = (text) => text.charAt(0).toUpperCase() + text.slice(1);
(async (args) => {
    let [box, amount] = args
    var name = JSON.parse(atob(localStorage.token.split('.')[1])).name,
        tokens = await fetch("https://api.blooket.com/api/users/tokens?name=" + name, {
            headers: {
                "referer": "https://www.blooket.com/",
                "content-type": "application/json",
                "authorization": localStorage.token
            }
        }),
        price = ({
            blizzard: 25,
            spooky: 25,
            aquatic: 25,
            bot: 20,
            space: 20,
            breakfast: 15,
            medieval: 15,
            wonderland: 20
        })[box],
        opens = amount > Math.floor(tokens / price) ? Math.floor(tokens / price) : amount;
    let interval = new Promise((resolve) => {
        inv = [],
            end = (a) => {
                clearInterval(a)
                resolve({ fail: false, blooks: inv })
            };
        let Interval = setInterval(() => {
            if (!opens) return end(Interval)
            fetch("https://api.blooket.com/api/users/unlockblook", {
                headers: {
                    authorization: localStorage.token,
                    "content-type": "application/json;charset=UTF-8",
                },
                referrer: "https://www.blooket.com/",
                body: JSON.stringify({ name, box }),
                method: "PUT"
            }).then(async (response) => {
                if (response.status != 200) return end(Interval);
                else inv.push(await response.json());
                opens--;
                if (!opens) return end(Interval)
            }).catch((e) => end(Interval));
        }, 128)
    });
    interval.then(async (x) => {
        if (x.fail) return alert("You don't have enough coins to open this box!");
        let count = {};
        Promise.all(x.blooks).then(Blooks => {
            Blooks.map(e => e.unlockedBlook).forEach((i) => {
                count[i] = (count[i] || 0) + 1;
            });
            alert('Results:\n' + Object.entries(count).map(x => `    ${x[1]} ${x[0]}`).join('\n'));

            blookValues = ({
                Toast: 5,
                Cereal: 5,
                Yogurt: 5,
                "Breakfast Combo": 5,
                "Orange Juice": 5,
                Milk: 5,
                Waffle: 20,
                Pancakes: 20,
                "French Toast": 75,
                Pizza: 75,
                Elf: 5,
                Witch: 5,
                Wizard: 5,
                Fairy: 5,
                "Slime Monster": 5,
                Jester: 20,
                Dragon: 20,
                Queen: 20,
                Unicorn: 75,
                King: 200,
                "Two of Spades": 5,
                "Eat Me": 5,
                "Drink Me": 5,
                Alice: 5,
                "Queen of Hearts": 5,
                Dormouse: 20,
                "White Rabbit": 20,
                "Cheshire Cat": 20,
                Caterpillar: 75,
                "Mad Hatter": 75,
                "King of Hearts": 200,
                Earth: 5,
                Meteor: 5,
                Stars: 5,
                Alien: 5,
                Planet: 20,
                UFO: 20,
                Spaceship: 75,
                Astronaut: 200,
                "Pink Astronaut": 300,
                "Yellow Astronaut": 300,
                "Black Astronaut": 300,
                "Orange Astronaut": 300,
                "Red Astronaut": 300,
                "Brown Astronaut": 300,
                "Green Astronaut": 300,
                "Lil Bot": 5,
                "Lovely Bot": 5,
                "Angry Bot": 5,
                "Happy Bot": 5,
                Watson: 20,
                "Buddy Bot": 20,
                "Brainy Bot": 75,
                "Mega Bot": 200,
                "Old Boot": 5,
                Jellyfish: 5,
                Clownfish: 5,
                Frog: 5,
                Crab: 5,
                Pufferfish: 20,
                Blobfish: 20,
                Octopus: 20,
                Narwhal: 75,
                "Baby Shark": 200,
                Megalodon: 250,
                Pumpkin: 5,
                "Swamp Monster": 5,
                Frankenstein: 5,
                Vampire: 5,
                Zombie: 20,
                Mummy: 20,
                Werewolf: 75,
                Ghost: 200,
                "Haunted Pumpkin": 300,
                "Snow Globe": 5,
                "Holiday Gift": 5,
                "Hot Chocolate": 5,
                "Holiday Wreath": 5,
                "Gingerbread Man": 20,
                "Gingerbread House": 20,
                Snowman: 75,
                "Santa Claus": 200,
                "Frost Wreath": 300,
                "Tropical Globe": 300

            });

            var totalValue = Number("0");

            for (const [blook, quant] of Object.entries(count)) {
                totalValue += (blookValues[blook]) * quant;
            };
            
            alert('Value of Blooks Unlocked: ' + totalValue);
        });
    });

})([((text) => text.charAt(0).toUpperCase() + text.slice(1))(prompt('What box do you want to open? (e.g. "Space") The limited boxes will not open if they are not available')), Number(prompt('How many boxes do you want to open?'))])

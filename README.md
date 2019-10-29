# PokeTypeCoverage
### Using a user-defined team of Pokémon, along with pokeapi.co, determine the team's move-list to provide maximum type coverage.


## How it works

1. Select each Pokémon from the Dropdown Search bar
2. (Optional) Select any moves you wish to keep (only moves with a Power rating are used in this calculation, so Swords Dance or Stealth Rock will never be picked).
3. Pick a desired minimum Power rating (default is 50)
4. Hit "Calculate"

And that's it!


## Logical Assumptions Made:

* All Pokémon will take their strongest STAB move. If dual-type, it will take one for each type.
* If a Pokémon's Base Stats indicate whether Attack or Special Attack are higher, the calculator will attempt to go for Physical or Special attacks accordingly. If a suitable move is not found, the Pokémon will drop one level in preference. If no other Pokémon can learn a suitable move of the currently desired type, it will loop back over with this rule ignored.
    * If a Pokémon's base stat indicates Attack and Special Attack are equal, it will try for Physical moves first, then Special.
* This is currently designed to loop with the Types in this current order, based on how well they do on offense:
    1. Ground
	2. Fighting
	3. Ghost or Dark
	   * If both are found, determine who can learn the stronger move. Offensively, these moves are Supereffective against the same types. Ghost is slightly prioritized because it has fewer Types that resist it.
    4. Ice
	5. Flying
	6. Grass
	7. Poison
	    * If a match has been found for all 7 of these, then there is a super-effective attack for every singular type in the game. The calculator will continue to move onward in order to account for dual-types nullifying a Super-effective. There are currently around a dozen Type combinations that meet this description.
	
	
	
##### Why are you doing this

Honestly to get a handle on React since I've been an Angular guy ever since it hit the scene, and I completely forgot to try out another framework.

Then when I was replaying Pokémon X/Y, trying to do a Nuzlocke challenge, I noticed while there were "Pick the Pokémon Types you have" calculators, they never accounted for movesets, which are the more important bit in my opinion. 

##### Any future plans to enhance this if it works?

I literately just started on this, I don't know. Maybe do some hard-coding to mark certain moves as "Less Desired", so that multi-turn stuff like Solarbeam doesn't get picked as an answer. Also try not to have it give a coverage move to a Pokémon where the type coverage is exclusively what it's weak to. Currently, we're be in a situation where it could consider giving Charizard Solarbeam, when they have a Slurpuff that can learn Energy Ball on its own.
The caculator also doesn't take things like Mega Evolutions into account.
Finally, with the amount of information crawling for Calculation, it's possible that this could turn into a strain on PokeAPI itself (Like most pristine APIs, it doesn't offer a documented way to actually query, so we're left asking for everything and going through it ourselves). On top of that, the way the data structured is sub-optimal for the specific use-case here. If it turns into a problem, this calculator would just move over to having its own local store for information.
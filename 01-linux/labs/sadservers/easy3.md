# Scenario: "The Command Line Murders"

## Description: Enter the name of the murderer in the file /home/admin/mysolution.

### Method
Everything in this solution has been worked out in ~/clmystery/mystery

Search for clues in the crimescene file, all information has been recorded but clues have been outlined with the heading "CLUE"
```
grep "CLUE" crimescene

CLUE: Footage from an ATM security camera is blurry but shows that the perpetrator is a tall male, at least 6'.
CLUE: Found a wallet believed to belong to the killer: no ID, just loose change, and membership cards for Rotary_Club, Delta SkyMiles, the local library, and the Museum of Bash History. The cards are totally untraceable and have no name, for some reason.
CLUE: Questioned the barista at the local coffee shop. He said a woman left right before they heard the shots. The name on her latte was Annabel.
```

Searched for the name 'Annabel'
```
grep 'Annabel' mystery/people

Annabel Church  F       38      Buckingham Place, line 179
Annabel Fuglsang        M       40      Haley Street, line 176
```

Used awk to jump to a specific line number in a street file to interview suspect
```
awk 'FNR == 179' ./mystery/streets/Buckingham_Place

SEE INTERVIEW 699607
```

Read the interview file
```
cat ./mystery/interviews/interview-699607

Interviewed Ms. Church at 2:04 pm.  Witness stated that she did not see anyone she could identify as the shooter, that she ran away as soon as the shots were fired.

However, she reports seeing the car that fled the scene.  Describes it as a blue Honda, with a license plate that starts with "L337" and ends with "9"
```

Searched vehicles with license plate starting with "L337"
```
grep -A 5 "L337" vehicles > car.txt
```

Narrowed down results to Honda cars and replaced car.txt with more accurate file
```
grep -A 5 "Honda" car.txt > car2.txt
rm car.txt
mv car2.txt car.txt

Make: Honda
Color: Blue
Owner: Jeremy Bowers
Height: 6'1

Make: Honda
Color: Blue
Owner: Joe Germuska
Height: 6'2
```
There were other results but given clues in the crimescene, these are prime suspects

Searched for their addresses and interview recording, same step as with original suspect previously. Clues highlighted that killer had membership cards for Rotary_Club, Delta SkyMiles, the local library, and the Museum of Bash History.

Checked if suspects had membership to these clubs with `grep`, only Joe Germuska was.

Submitted prime suspect to complete solution
```
echo 'Joe Germuska' > /mysolution
```

**What I learned:** `grep -A `and `-B` show a number of lines after and before a matched pattern respectively. `awk 'FNR = N'` tells it to print only line number 'N' from a file.




Coding the Humanities exam
In this exam, you will engage with 3 sections:

Reading song lyrics (40pts): you will here have to read some lyrics into memory and prepare them for analysis.
Analysing song lyrics (40pts): you will analyse the results of step 1.
Analysing more song lyrics (20pts): for a higher grade, you will work with a larger dataset of song lyrics with Pandas.
You are expected to briefly explain what you are doing in markdown and by commenting your code.

Bonueses:

Up to 10pts for particularly good code and documentation.
Up to 10pts for creativity (if you dore more than I expect in a creative way).
Therefore the total number of points you can accumulate is 120, but the grade is calculated with a maximum of 100. Lucky you.

Instructions
After you have downloaded the zip archive from Canvas and unzipped it locally, work in the Exam.ipynb notebook using your preferred environment. All the questions for the exam are there. Make sure to add your name and student id to the notebook too.
When you are done coding and you are happy with your results, make sure to run all cells again from the first to the last, then save your notebook.
Click on File > Download as > .hmtl and save the html export into the exam's folder.
Close your notebook.
Rename the exam folder with your surname and student id. For example: colavizza_123456.zip.
Compress the exam folder with your work into a zip archive and upload it on Canvas.
Dataset
For this exam, you will be working with the Billboard pop music lyrics dataset. Billboard has published a Year-End Hot 100 every December since 1958. The data for the exam has been borrowed from this repository. You can read an analysis of the same dataset in this Medium post.

Yourself
Please add this info before your start:

Name: Helge Moes
Student ID: 11348801
Reading song lyrics (40pts)
In the folder data/selected, you can find the songs from the band U2 part of the dataset you are working with.

Create an NLP pipeline that does the following:

Read all songs into memory and save them into a dictionary, with the name of the song (and of the files) as key, and the song lyrics as value.
Tokenize all lyrics and apply some filtering operation (you chose what to filter, make sure to motivate your choice).
# To figure out where to retrieve my data, I used the getcwd to demonstrate where the data was stored
from os import getcwd
getcwd()
#/Users/Helge?Desktop?CdH_exam_1
'/Users/Helge/Desktop/CdH_exam_1'
# The dictionary is named the_U2_list, every song is set as key, such as 'beautiful_day'. Besides that, each value are the lyrics of the specific song.
# I used this in at the start, since I was not able te retrieve the dataset from the designated file
the_U2_list = {'beautiful_day': 'the heart is a bloom shoots up through the stony ground theres no room no space to rent in this townyoure out of luck and the reason that you had to care the traffic is stuck and youre not moving anywhereyou thought youd found a friend to take you out of this place someone you could lend a hand in return for graceits a beautiful day sky falls you feel like its a beautiful day dont let it get awayyoure on the road but youve got no destination youre in the mud in the maze of her imaginationyoure lovin this town even if that doesnt ring true youve been all over and its been all over youits a beautiful day dont let it get away its a beautiful daytouch me take me to that other place teach me i know im not a hopeless casesee the world in green and blue see china right in front of you see the canyons broken by cloud see the tuna fleets clearing the sea out see the bedouin fires at night see the oil fields at first light and see the bird with a leaf in her mouth after the flood all the colors came outit was a beautiful day dont let it get away beautiful daytouch me take me to that other place reach me i know im not a hopeless casewhat you dont have you dont need it now what you dont know you can feel it somehow what you dont have you dont need it now dont need it now was a beautiful day', 
           'desire': 'yeah lover im off the streets gonna go where the bright lights and the big city meet with a red guitar on fire desireshes the candle burning in my room im like the needle needle and spoon over the counter with a shotgun pretty soon everybody got one and the fever when im beside her desire desiredesire desireburning burning', 
           'one': 'is it getting better or do you feel the same will it make it easier on you now you got someone to blameyou say one love one life when its one need in the night its one love we get to share it it leaves you baby if you dont care for itdid i disappoint you or leave a bad taste in your mouth you act like you never had love and you want me to go withoutwell its too late tonight to drag the past out into the light were one but were not the same we get to carry each other carry each other onehave you come here for forgiveness have you come to raise the dead have you come here to play jesus to the lepers in your head did i ask too much more than a lot you gave me nothing now its all i got were one but were not the same we hurt each other then we do it againyou say love is a temple love a higher law love is a temple love the higher law you ask me to enter but then you made me crawl and i cant be holding on to what you got when all you got is hurtone love one blood one life you got to do what you shouldone life with each other sisters brothersone life but were not the same we get to carry each other carry each otheroneone', 
           'with_or_without_you': 'see the stone set in your eyes see the thorn twist in your side i wait for you sleight of hand and twist of fate on a bed of nails she makes me wait and i wait without youwith or without you with or without youthrough the storm we reach the shore you give it all but i want more and im waiting for youwith or without you with or without you i cant live with or without youand you give yourself away and you give yourself away and you give and you give and you give yourself awaymy hands are tied my body bruised shes got me with nothing to win and nothing left to loseand you give yourself away and you give yourself away and you give and you give and you give yourself awaywith or without you with or without you i cant live with or without you ohwith or without you with or without you i cant live with or without youwith or without you', 
           'mysterious_ways': 'johnny take a walk with your sister the moon let her pale light in to fill up your room youve been living underground eating from a can youve been running away from what you dont understand loveshes slippy youre sliding down shell be there when you hit the groundits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious waysjohnny take a dive with your sister in the rain let her talk about the things you cant explain to touch is to heal to hurt is to steal if you want to kiss the sky better learn how to kneel on your knees boyshes the wave she turns the tide she sees the man inside the child yeahits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways its alright its alright its alright lift my days light up my nightsone day youll look back and when you see where you were held how by this love while you could stand there you could move on this moment follow this feelingits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways ah oh oh ah huh move move move move she moves with it she moves me like lift my days and light up my nights love', 
           'i_still-havent_found_what_i_am_looking_for': 'i have climbed the highest mountains i have run through the fields only to be with you only to be with youi have run i have crawled i have scaled these city walls these city walls only to be with you but i still havent found what im looking for but i still havent found what im looking fori have kissed honey lips felt the healing in the fingertips it burned like fire this burning desire i have spoke with the tongue of angels i have held the hand of a devil it was warm in the night i was cold as a stone but i still havent found what im looking for but i still havent found what im looking fori believe in the kingdom come then all the colors will bleed into one bleed into one but yes im still running you broke the bonds and you you loosened the chains you carried the cross of my shame oh my shame you know i believe it but i still havent found what im looking for but i still havent found what im looking for', 
           'hold_me_thrill_me_kiss_me_kill_me': 'you dont know how you took it you just know what you got oh lordy youve been stealing from the thieves and you got caughtin the headlights of a stretch car youre a stardressing like your sister living like a tart they dont know what youre doing babe it must be artyoure a headache in a suitcase youre a staroh no dont be shy you dont have to go blind hold me thrill me kiss me kill meyou dont know how you got here you just know you want out believing in yourself almost as much as you doubtyoure a big smash you wear it like a rash staroh no dont be shy it takes a crowd to cry hold me thrill me kiss me kill methey want you to be jesus theyll go down on one knee but theyll want their money back if youre alive at thirtythreeand youre turning tricks with your crucifix youre a star oh childof course youre not shy you dont have to deny love hold me thrill me kiss me kill me'}
    
# To check whether this part works, the song 'one' is printed. It resulted in an output that showed the lyrics.
print(the_U2_list['one'])
is it getting better or do you feel the same will it make it easier on you now you got someone to blameyou say one love one life when its one need in the night its one love we get to share it it leaves you baby if you dont care for itdid i disappoint you or leave a bad taste in your mouth you act like you never had love and you want me to go withoutwell its too late tonight to drag the past out into the light were one but were not the same we get to carry each other carry each other onehave you come here for forgiveness have you come to raise the dead have you come here to play jesus to the lepers in your head did i ask too much more than a lot you gave me nothing now its all i got were one but were not the same we hurt each other then we do it againyou say love is a temple love a higher law love is a temple love the higher law you ask me to enter but then you made me crawl and i cant be holding on to what you got when all you got is hurtone love one blood one life you got to do what you shouldone life with each other sisters brothersone life but were not the same we get to carry each other carry each otheroneone
# To see the songs in a coherent fashion, the next function is used
print(the_U2_list.keys())
['desire', 'i_still-havent_found_what_i_am_looking_for', 'one', 'hold_me_thrill_me_kiss_me_kill_me', 'with_or_without_you', 'mysterious_ways', 'beautiful_day']
# This import method did not seem to work, due to my directory, therefore I tried another method to see if it might work
import csv
with open("C:\Users\Helge\Desktop\CdH_exam_1\one.txt", 'r') as csv.file:
    U2_csv = csv.reader(csv.file)
    for line in U2_csv:
        print(line)
---------------------------------------------------------------------------
IOError                                   Traceback (most recent call last)
<ipython-input-63-c0d9dae7b76b> in <module>()
      1 import csv
----> 2 with open("C:\Users\Helge\Desktop\CdH_exam_1\one.txt", 'r') as csv.file:
      3     U2_csv = csv.reader(csv.file)
      4     for line in U2_csv:
      5         print(line)

IOError: [Errno 2] No such file or directory: 'C:\\Users\\Helge\\Desktop\\CdH_exam_1\\one.txt'
# I decided to individually import each file from the data/selected file to make sure that it would not contain an error while putting it in a dictionary
import os
import nltk
U2_list = os.listdir("data/selected/")
print(U2_list)

file1 = open("data/selected/beautiful_day.txt", "r")
U2_1 = file1.read()
file1.close()

file2 = open("data/selected/one.txt", "r")
U2_2 = file2.read()
file2.close()

file3 = open("data/selected/desire.txt", "r")
U2_3 = file3.read()
file3.close()

file4 = open("data/selected/hold_me_thrill_me_kiss_me_kill_me.txt", "r")
U2_4 = file4.read()
file4.close()

file5 = open("data/selected/i_still_havent_found_what_im_looking_for.txt", "r")
U2_5 = file5.read()
file5.close()

file6 = open("data/selected/with_or_without_you.txt", "r")
U2_6 = file6.read()
file6.close()

file7 = open("data/selected/mysterious_ways.txt", "r")
U2_7 = file7.read()
file7.close()
['.DS_Store', 'beautiful_day.txt', 'desire.txt', 'hold_me_thrill_me_kiss_me_kill_me.txt', 'i_still_havent_found_what_im_looking_for.txt', 'mysterious_ways.txt', 'one.txt', 'with_or_without_you.txt']
# The dictionary allows for the retrieval of the lyrics autonomously from the file
print(U2_6)
see the stone set in your eyes see the thorn twist in your side i wait for you sleight of hand and twist of fate on a bed of nails she makes me wait and i wait without youwith or without you with or without youthrough the storm we reach the shore you give it all but i want more and im waiting for youwith or without you with or without you i cant live with or without youand you give yourself away and you give yourself away and you give and you give and you give yourself awaymy hands are tied my body bruised shes got me with nothing to win and nothing left to loseand you give yourself away and you give yourself away and you give and you give and you give yourself awaywith or without you with or without you i cant live with or without you ohwith or without you with or without you i cant live with or without youwith or without you
# A list of songs is created, as to assess the words within the U2 songs, it is saved as a dictionary where U2 is the key
U2_Songs = []
U2_Songs.extend([U2_1, U2_2, U2_3, U2_4, U2_5, U2_5, U2_6, U2_7])

new_dictionary = dict(zip(U2_list, U2_Songs))
# All the songs are put together
print(U2_Songs)
['the heart is a bloom shoots up through the stony ground theres no room no space to rent in this townyoure out of luck and the reason that you had to care the traffic is stuck and youre not moving anywhereyou thought youd found a friend to take you out of this place someone you could lend a hand in return for graceits a beautiful day sky falls you feel like its a beautiful day dont let it get awayyoure on the road but youve got no destination youre in the mud in the maze of her imaginationyoure lovin this town even if that doesnt ring true youve been all over and its been all over youits a beautiful day dont let it get away its a beautiful daytouch me take me to that other place teach me i know im not a hopeless casesee the world in green and blue see china right in front of you see the canyons broken by cloud see the tuna fleets clearing the sea out see the bedouin fires at night see the oil fields at first light and see the bird with a leaf in her mouth after the flood all the colors came outit was a beautiful day dont let it get away beautiful daytouch me take me to that other place reach me i know im not a hopeless casewhat you dont have you dont need it now what you dont know you can feel it somehow what you dont have you dont need it now dont need it now was a beautiful day', 'is it getting better or do you feel the same will it make it easier on you now you got someone to blameyou say one love one life when its one need in the night its one love we get to share it it leaves you baby if you dont care for itdid i disappoint you or leave a bad taste in your mouth you act like you never had love and you want me to go withoutwell its too late tonight to drag the past out into the light were one but were not the same we get to carry each other carry each other onehave you come here for forgiveness have you come to raise the dead have you come here to play jesus to the lepers in your head did i ask too much more than a lot you gave me nothing now its all i got were one but were not the same we hurt each other then we do it againyou say love is a temple love a higher law love is a temple love the higher law you ask me to enter but then you made me crawl and i cant be holding on to what you got when all you got is hurtone love one blood one life you got to do what you shouldone life with each other sisters brothersone life but were not the same we get to carry each other carry each otheroneone', 'yeah lover im off the streets gonna go where the bright lights and the big city meet with a red guitar on fire desireshes the candle burning in my room im like the needle needle and spoon over the counter with a shotgun pretty soon everybody got one and the fever when im beside her desire desiredesire desireburning burning', 'you dont know how you took it you just know what you got oh lordy youve been stealing from the thieves and you got caughtin the headlights of a stretch car youre a stardressing like your sister living like a tart they dont know what youre doing babe it must be artyoure a headache in a suitcase youre a staroh no dont be shy you dont have to go blind hold me thrill me kiss me kill meyou dont know how you got here you just know you want out believing in yourself almost as much as you doubtyoure a big smash you wear it like a rash staroh no dont be shy it takes a crowd to cry hold me thrill me kiss me kill methey want you to be jesus theyll go down on one knee but theyll want their money back if youre alive at thirtythreeand youre turning tricks with your crucifix youre a star oh childof course youre not shy you dont have to deny love hold me thrill me kiss me kill me', 'i have climbed the highest mountains i have run through the fields only to be with you only to be with youi have run i have crawled i have scaled these city walls these city walls only to be with you but i still havent found what im looking for but i still havent found what im looking fori have kissed honey lips felt the healing in the fingertips it burned like fire this burning desire i have spoke with the tongue of angels i have held the hand of a devil it was warm in the night i was cold as a stone but i still havent found what im looking for but i still havent found what im looking fori believe in the kingdom come then all the colors will bleed into one bleed into one but yes im still running you broke the bonds and you you loosened the chains you carried the cross of my shame oh my shame you know i believe it but i still havent found what im looking for but i still havent found what im looking for', 'i have climbed the highest mountains i have run through the fields only to be with you only to be with youi have run i have crawled i have scaled these city walls these city walls only to be with you but i still havent found what im looking for but i still havent found what im looking fori have kissed honey lips felt the healing in the fingertips it burned like fire this burning desire i have spoke with the tongue of angels i have held the hand of a devil it was warm in the night i was cold as a stone but i still havent found what im looking for but i still havent found what im looking fori believe in the kingdom come then all the colors will bleed into one bleed into one but yes im still running you broke the bonds and you you loosened the chains you carried the cross of my shame oh my shame you know i believe it but i still havent found what im looking for but i still havent found what im looking for', 'see the stone set in your eyes see the thorn twist in your side i wait for you sleight of hand and twist of fate on a bed of nails she makes me wait and i wait without youwith or without you with or without youthrough the storm we reach the shore you give it all but i want more and im waiting for youwith or without you with or without you i cant live with or without youand you give yourself away and you give yourself away and you give and you give and you give yourself awaymy hands are tied my body bruised shes got me with nothing to win and nothing left to loseand you give yourself away and you give yourself away and you give and you give and you give yourself awaywith or without you with or without you i cant live with or without you ohwith or without you with or without you i cant live with or without youwith or without you', 'johnny take a walk with your sister the moon let her pale light in to fill up your room youve been living underground eating from a can youve been running away from what you dont understand loveshes slippy youre sliding down shell be there when you hit the groundits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious waysjohnny take a dive with your sister in the rain let her talk about the things you cant explain to touch is to heal to hurt is to steal if you want to kiss the sky better learn how to kneel on your knees boyshes the wave she turns the tide she sees the man inside the child yeahits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways its alright its alright its alright lift my days light up my nightsone day youll look back and when you see where you were held how by this love while you could stand there you could move on this moment follow this feelingits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways ah oh oh ah huh move move move move she moves with it she moves me like lift my days and light up my nights love']
# Here the combined songteksts are joined to a string
string = ""
Album = string.join(U2_Songs)
print(Album)
the heart is a bloom shoots up through the stony ground theres no room no space to rent in this townyoure out of luck and the reason that you had to care the traffic is stuck and youre not moving anywhereyou thought youd found a friend to take you out of this place someone you could lend a hand in return for graceits a beautiful day sky falls you feel like its a beautiful day dont let it get awayyoure on the road but youve got no destination youre in the mud in the maze of her imaginationyoure lovin this town even if that doesnt ring true youve been all over and its been all over youits a beautiful day dont let it get away its a beautiful daytouch me take me to that other place teach me i know im not a hopeless casesee the world in green and blue see china right in front of you see the canyons broken by cloud see the tuna fleets clearing the sea out see the bedouin fires at night see the oil fields at first light and see the bird with a leaf in her mouth after the flood all the colors came outit was a beautiful day dont let it get away beautiful daytouch me take me to that other place reach me i know im not a hopeless casewhat you dont have you dont need it now what you dont know you can feel it somehow what you dont have you dont need it now dont need it now was a beautiful dayis it getting better or do you feel the same will it make it easier on you now you got someone to blameyou say one love one life when its one need in the night its one love we get to share it it leaves you baby if you dont care for itdid i disappoint you or leave a bad taste in your mouth you act like you never had love and you want me to go withoutwell its too late tonight to drag the past out into the light were one but were not the same we get to carry each other carry each other onehave you come here for forgiveness have you come to raise the dead have you come here to play jesus to the lepers in your head did i ask too much more than a lot you gave me nothing now its all i got were one but were not the same we hurt each other then we do it againyou say love is a temple love a higher law love is a temple love the higher law you ask me to enter but then you made me crawl and i cant be holding on to what you got when all you got is hurtone love one blood one life you got to do what you shouldone life with each other sisters brothersone life but were not the same we get to carry each other carry each otheroneoneyeah lover im off the streets gonna go where the bright lights and the big city meet with a red guitar on fire desireshes the candle burning in my room im like the needle needle and spoon over the counter with a shotgun pretty soon everybody got one and the fever when im beside her desire desiredesire desireburning burningyou dont know how you took it you just know what you got oh lordy youve been stealing from the thieves and you got caughtin the headlights of a stretch car youre a stardressing like your sister living like a tart they dont know what youre doing babe it must be artyoure a headache in a suitcase youre a staroh no dont be shy you dont have to go blind hold me thrill me kiss me kill meyou dont know how you got here you just know you want out believing in yourself almost as much as you doubtyoure a big smash you wear it like a rash staroh no dont be shy it takes a crowd to cry hold me thrill me kiss me kill methey want you to be jesus theyll go down on one knee but theyll want their money back if youre alive at thirtythreeand youre turning tricks with your crucifix youre a star oh childof course youre not shy you dont have to deny love hold me thrill me kiss me kill mei have climbed the highest mountains i have run through the fields only to be with you only to be with youi have run i have crawled i have scaled these city walls these city walls only to be with you but i still havent found what im looking for but i still havent found what im looking fori have kissed honey lips felt the healing in the fingertips it burned like fire this burning desire i have spoke with the tongue of angels i have held the hand of a devil it was warm in the night i was cold as a stone but i still havent found what im looking for but i still havent found what im looking fori believe in the kingdom come then all the colors will bleed into one bleed into one but yes im still running you broke the bonds and you you loosened the chains you carried the cross of my shame oh my shame you know i believe it but i still havent found what im looking for but i still havent found what im looking fori have climbed the highest mountains i have run through the fields only to be with you only to be with youi have run i have crawled i have scaled these city walls these city walls only to be with you but i still havent found what im looking for but i still havent found what im looking fori have kissed honey lips felt the healing in the fingertips it burned like fire this burning desire i have spoke with the tongue of angels i have held the hand of a devil it was warm in the night i was cold as a stone but i still havent found what im looking for but i still havent found what im looking fori believe in the kingdom come then all the colors will bleed into one bleed into one but yes im still running you broke the bonds and you you loosened the chains you carried the cross of my shame oh my shame you know i believe it but i still havent found what im looking for but i still havent found what im looking forsee the stone set in your eyes see the thorn twist in your side i wait for you sleight of hand and twist of fate on a bed of nails she makes me wait and i wait without youwith or without you with or without youthrough the storm we reach the shore you give it all but i want more and im waiting for youwith or without you with or without you i cant live with or without youand you give yourself away and you give yourself away and you give and you give and you give yourself awaymy hands are tied my body bruised shes got me with nothing to win and nothing left to loseand you give yourself away and you give yourself away and you give and you give and you give yourself awaywith or without you with or without you i cant live with or without you ohwith or without you with or without you i cant live with or without youwith or without youjohnny take a walk with your sister the moon let her pale light in to fill up your room youve been living underground eating from a can youve been running away from what you dont understand loveshes slippy youre sliding down shell be there when you hit the groundits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious waysjohnny take a dive with your sister in the rain let her talk about the things you cant explain to touch is to heal to hurt is to steal if you want to kiss the sky better learn how to kneel on your knees boyshes the wave she turns the tide she sees the man inside the child yeahits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways its alright its alright its alright lift my days light up my nightsone day youll look back and when you see where you were held how by this love while you could stand there you could move on this moment follow this feelingits alright its alright its alright she moves in mysterious ways its alright its alright its alright she moves in mysterious ways ah oh oh ah huh move move move move she moves with it she moves me like lift my days and light up my nights love
# On the webpage; https://stackoverflow.com/questions/37101114/what-to-download-in-order-to-make-nltk-tokenize-word-tokenize-work/37101713
# I found that 'punkt' was able to download and run the word tokenization, this was probably due to my initial problem of not being able to transfer the files in the beginning

import nltk
nltk.download('punkt')
from nltk.tokenize import word_tokenize
[nltk_data] Downloading package punkt to /Users/Helge/nltk_data...
[nltk_data]   Unzipping tokenizers/punkt.zip.
# To tokenize all the lyrics together, the following came to existence
Album_t = word_tokenize(Album)
print(Album_t)
['the', 'heart', 'is', 'a', 'bloom', 'shoots', 'up', 'through', 'the', 'stony', 'ground', 'theres', 'no', 'room', 'no', 'space', 'to', 'rent', 'in', 'this', 'townyoure', 'out', 'of', 'luck', 'and', 'the', 'reason', 'that', 'you', 'had', 'to', 'care', 'the', 'traffic', 'is', 'stuck', 'and', 'youre', 'not', 'moving', 'anywhereyou', 'thought', 'youd', 'found', 'a', 'friend', 'to', 'take', 'you', 'out', 'of', 'this', 'place', 'someone', 'you', 'could', 'lend', 'a', 'hand', 'in', 'return', 'for', 'graceits', 'a', 'beautiful', 'day', 'sky', 'falls', 'you', 'feel', 'like', 'its', 'a', 'beautiful', 'day', 'dont', 'let', 'it', 'get', 'awayyoure', 'on', 'the', 'road', 'but', 'youve', 'got', 'no', 'destination', 'youre', 'in', 'the', 'mud', 'in', 'the', 'maze', 'of', 'her', 'imaginationyoure', 'lovin', 'this', 'town', 'even', 'if', 'that', 'doesnt', 'ring', 'true', 'youve', 'been', 'all', 'over', 'and', 'its', 'been', 'all', 'over', 'youits', 'a', 'beautiful', 'day', 'dont', 'let', 'it', 'get', 'away', 'its', 'a', 'beautiful', 'daytouch', 'me', 'take', 'me', 'to', 'that', 'other', 'place', 'teach', 'me', 'i', 'know', 'im', 'not', 'a', 'hopeless', 'casesee', 'the', 'world', 'in', 'green', 'and', 'blue', 'see', 'china', 'right', 'in', 'front', 'of', 'you', 'see', 'the', 'canyons', 'broken', 'by', 'cloud', 'see', 'the', 'tuna', 'fleets', 'clearing', 'the', 'sea', 'out', 'see', 'the', 'bedouin', 'fires', 'at', 'night', 'see', 'the', 'oil', 'fields', 'at', 'first', 'light', 'and', 'see', 'the', 'bird', 'with', 'a', 'leaf', 'in', 'her', 'mouth', 'after', 'the', 'flood', 'all', 'the', 'colors', 'came', 'outit', 'was', 'a', 'beautiful', 'day', 'dont', 'let', 'it', 'get', 'away', 'beautiful', 'daytouch', 'me', 'take', 'me', 'to', 'that', 'other', 'place', 'reach', 'me', 'i', 'know', 'im', 'not', 'a', 'hopeless', 'casewhat', 'you', 'dont', 'have', 'you', 'dont', 'need', 'it', 'now', 'what', 'you', 'dont', 'know', 'you', 'can', 'feel', 'it', 'somehow', 'what', 'you', 'dont', 'have', 'you', 'dont', 'need', 'it', 'now', 'dont', 'need', 'it', 'now', 'was', 'a', 'beautiful', 'dayis', 'it', 'getting', 'better', 'or', 'do', 'you', 'feel', 'the', 'same', 'will', 'it', 'make', 'it', 'easier', 'on', 'you', 'now', 'you', 'got', 'someone', 'to', 'blameyou', 'say', 'one', 'love', 'one', 'life', 'when', 'its', 'one', 'need', 'in', 'the', 'night', 'its', 'one', 'love', 'we', 'get', 'to', 'share', 'it', 'it', 'leaves', 'you', 'baby', 'if', 'you', 'dont', 'care', 'for', 'itdid', 'i', 'disappoint', 'you', 'or', 'leave', 'a', 'bad', 'taste', 'in', 'your', 'mouth', 'you', 'act', 'like', 'you', 'never', 'had', 'love', 'and', 'you', 'want', 'me', 'to', 'go', 'withoutwell', 'its', 'too', 'late', 'tonight', 'to', 'drag', 'the', 'past', 'out', 'into', 'the', 'light', 'were', 'one', 'but', 'were', 'not', 'the', 'same', 'we', 'get', 'to', 'carry', 'each', 'other', 'carry', 'each', 'other', 'onehave', 'you', 'come', 'here', 'for', 'forgiveness', 'have', 'you', 'come', 'to', 'raise', 'the', 'dead', 'have', 'you', 'come', 'here', 'to', 'play', 'jesus', 'to', 'the', 'lepers', 'in', 'your', 'head', 'did', 'i', 'ask', 'too', 'much', 'more', 'than', 'a', 'lot', 'you', 'gave', 'me', 'nothing', 'now', 'its', 'all', 'i', 'got', 'were', 'one', 'but', 'were', 'not', 'the', 'same', 'we', 'hurt', 'each', 'other', 'then', 'we', 'do', 'it', 'againyou', 'say', 'love', 'is', 'a', 'temple', 'love', 'a', 'higher', 'law', 'love', 'is', 'a', 'temple', 'love', 'the', 'higher', 'law', 'you', 'ask', 'me', 'to', 'enter', 'but', 'then', 'you', 'made', 'me', 'crawl', 'and', 'i', 'cant', 'be', 'holding', 'on', 'to', 'what', 'you', 'got', 'when', 'all', 'you', 'got', 'is', 'hurtone', 'love', 'one', 'blood', 'one', 'life', 'you', 'got', 'to', 'do', 'what', 'you', 'shouldone', 'life', 'with', 'each', 'other', 'sisters', 'brothersone', 'life', 'but', 'were', 'not', 'the', 'same', 'we', 'get', 'to', 'carry', 'each', 'other', 'carry', 'each', 'otheroneoneyeah', 'lover', 'im', 'off', 'the', 'streets', 'gon', 'na', 'go', 'where', 'the', 'bright', 'lights', 'and', 'the', 'big', 'city', 'meet', 'with', 'a', 'red', 'guitar', 'on', 'fire', 'desireshes', 'the', 'candle', 'burning', 'in', 'my', 'room', 'im', 'like', 'the', 'needle', 'needle', 'and', 'spoon', 'over', 'the', 'counter', 'with', 'a', 'shotgun', 'pretty', 'soon', 'everybody', 'got', 'one', 'and', 'the', 'fever', 'when', 'im', 'beside', 'her', 'desire', 'desiredesire', 'desireburning', 'burningyou', 'dont', 'know', 'how', 'you', 'took', 'it', 'you', 'just', 'know', 'what', 'you', 'got', 'oh', 'lordy', 'youve', 'been', 'stealing', 'from', 'the', 'thieves', 'and', 'you', 'got', 'caughtin', 'the', 'headlights', 'of', 'a', 'stretch', 'car', 'youre', 'a', 'stardressing', 'like', 'your', 'sister', 'living', 'like', 'a', 'tart', 'they', 'dont', 'know', 'what', 'youre', 'doing', 'babe', 'it', 'must', 'be', 'artyoure', 'a', 'headache', 'in', 'a', 'suitcase', 'youre', 'a', 'staroh', 'no', 'dont', 'be', 'shy', 'you', 'dont', 'have', 'to', 'go', 'blind', 'hold', 'me', 'thrill', 'me', 'kiss', 'me', 'kill', 'meyou', 'dont', 'know', 'how', 'you', 'got', 'here', 'you', 'just', 'know', 'you', 'want', 'out', 'believing', 'in', 'yourself', 'almost', 'as', 'much', 'as', 'you', 'doubtyoure', 'a', 'big', 'smash', 'you', 'wear', 'it', 'like', 'a', 'rash', 'staroh', 'no', 'dont', 'be', 'shy', 'it', 'takes', 'a', 'crowd', 'to', 'cry', 'hold', 'me', 'thrill', 'me', 'kiss', 'me', 'kill', 'methey', 'want', 'you', 'to', 'be', 'jesus', 'theyll', 'go', 'down', 'on', 'one', 'knee', 'but', 'theyll', 'want', 'their', 'money', 'back', 'if', 'youre', 'alive', 'at', 'thirtythreeand', 'youre', 'turning', 'tricks', 'with', 'your', 'crucifix', 'youre', 'a', 'star', 'oh', 'childof', 'course', 'youre', 'not', 'shy', 'you', 'dont', 'have', 'to', 'deny', 'love', 'hold', 'me', 'thrill', 'me', 'kiss', 'me', 'kill', 'mei', 'have', 'climbed', 'the', 'highest', 'mountains', 'i', 'have', 'run', 'through', 'the', 'fields', 'only', 'to', 'be', 'with', 'you', 'only', 'to', 'be', 'with', 'youi', 'have', 'run', 'i', 'have', 'crawled', 'i', 'have', 'scaled', 'these', 'city', 'walls', 'these', 'city', 'walls', 'only', 'to', 'be', 'with', 'you', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'fori', 'have', 'kissed', 'honey', 'lips', 'felt', 'the', 'healing', 'in', 'the', 'fingertips', 'it', 'burned', 'like', 'fire', 'this', 'burning', 'desire', 'i', 'have', 'spoke', 'with', 'the', 'tongue', 'of', 'angels', 'i', 'have', 'held', 'the', 'hand', 'of', 'a', 'devil', 'it', 'was', 'warm', 'in', 'the', 'night', 'i', 'was', 'cold', 'as', 'a', 'stone', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'fori', 'believe', 'in', 'the', 'kingdom', 'come', 'then', 'all', 'the', 'colors', 'will', 'bleed', 'into', 'one', 'bleed', 'into', 'one', 'but', 'yes', 'im', 'still', 'running', 'you', 'broke', 'the', 'bonds', 'and', 'you', 'you', 'loosened', 'the', 'chains', 'you', 'carried', 'the', 'cross', 'of', 'my', 'shame', 'oh', 'my', 'shame', 'you', 'know', 'i', 'believe', 'it', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'fori', 'have', 'climbed', 'the', 'highest', 'mountains', 'i', 'have', 'run', 'through', 'the', 'fields', 'only', 'to', 'be', 'with', 'you', 'only', 'to', 'be', 'with', 'youi', 'have', 'run', 'i', 'have', 'crawled', 'i', 'have', 'scaled', 'these', 'city', 'walls', 'these', 'city', 'walls', 'only', 'to', 'be', 'with', 'you', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'fori', 'have', 'kissed', 'honey', 'lips', 'felt', 'the', 'healing', 'in', 'the', 'fingertips', 'it', 'burned', 'like', 'fire', 'this', 'burning', 'desire', 'i', 'have', 'spoke', 'with', 'the', 'tongue', 'of', 'angels', 'i', 'have', 'held', 'the', 'hand', 'of', 'a', 'devil', 'it', 'was', 'warm', 'in', 'the', 'night', 'i', 'was', 'cold', 'as', 'a', 'stone', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'fori', 'believe', 'in', 'the', 'kingdom', 'come', 'then', 'all', 'the', 'colors', 'will', 'bleed', 'into', 'one', 'bleed', 'into', 'one', 'but', 'yes', 'im', 'still', 'running', 'you', 'broke', 'the', 'bonds', 'and', 'you', 'you', 'loosened', 'the', 'chains', 'you', 'carried', 'the', 'cross', 'of', 'my', 'shame', 'oh', 'my', 'shame', 'you', 'know', 'i', 'believe', 'it', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'for', 'but', 'i', 'still', 'havent', 'found', 'what', 'im', 'looking', 'forsee', 'the', 'stone', 'set', 'in', 'your', 'eyes', 'see', 'the', 'thorn', 'twist', 'in', 'your', 'side', 'i', 'wait', 'for', 'you', 'sleight', 'of', 'hand', 'and', 'twist', 'of', 'fate', 'on', 'a', 'bed', 'of', 'nails', 'she', 'makes', 'me', 'wait', 'and', 'i', 'wait', 'without', 'youwith', 'or', 'without', 'you', 'with', 'or', 'without', 'youthrough', 'the', 'storm', 'we', 'reach', 'the', 'shore', 'you', 'give', 'it', 'all', 'but', 'i', 'want', 'more', 'and', 'im', 'waiting', 'for', 'youwith', 'or', 'without', 'you', 'with', 'or', 'without', 'you', 'i', 'cant', 'live', 'with', 'or', 'without', 'youand', 'you', 'give', 'yourself', 'away', 'and', 'you', 'give', 'yourself', 'away', 'and', 'you', 'give', 'and', 'you', 'give', 'and', 'you', 'give', 'yourself', 'awaymy', 'hands', 'are', 'tied', 'my', 'body', 'bruised', 'shes', 'got', 'me', 'with', 'nothing', 'to', 'win', 'and', 'nothing', 'left', 'to', 'loseand', 'you', 'give', 'yourself', 'away', 'and', 'you', 'give', 'yourself', 'away', 'and', 'you', 'give', 'and', 'you', 'give', 'and', 'you', 'give', 'yourself', 'awaywith', 'or', 'without', 'you', 'with', 'or', 'without', 'you', 'i', 'cant', 'live', 'with', 'or', 'without', 'you', 'ohwith', 'or', 'without', 'you', 'with', 'or', 'without', 'you', 'i', 'cant', 'live', 'with', 'or', 'without', 'youwith', 'or', 'without', 'youjohnny', 'take', 'a', 'walk', 'with', 'your', 'sister', 'the', 'moon', 'let', 'her', 'pale', 'light', 'in', 'to', 'fill', 'up', 'your', 'room', 'youve', 'been', 'living', 'underground', 'eating', 'from', 'a', 'can', 'youve', 'been', 'running', 'away', 'from', 'what', 'you', 'dont', 'understand', 'loveshes', 'slippy', 'youre', 'sliding', 'down', 'shell', 'be', 'there', 'when', 'you', 'hit', 'the', 'groundits', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'ways', 'its', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'waysjohnny', 'take', 'a', 'dive', 'with', 'your', 'sister', 'in', 'the', 'rain', 'let', 'her', 'talk', 'about', 'the', 'things', 'you', 'cant', 'explain', 'to', 'touch', 'is', 'to', 'heal', 'to', 'hurt', 'is', 'to', 'steal', 'if', 'you', 'want', 'to', 'kiss', 'the', 'sky', 'better', 'learn', 'how', 'to', 'kneel', 'on', 'your', 'knees', 'boyshes', 'the', 'wave', 'she', 'turns', 'the', 'tide', 'she', 'sees', 'the', 'man', 'inside', 'the', 'child', 'yeahits', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'ways', 'its', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'ways', 'its', 'alright', 'its', 'alright', 'its', 'alright', 'lift', 'my', 'days', 'light', 'up', 'my', 'nightsone', 'day', 'youll', 'look', 'back', 'and', 'when', 'you', 'see', 'where', 'you', 'were', 'held', 'how', 'by', 'this', 'love', 'while', 'you', 'could', 'stand', 'there', 'you', 'could', 'move', 'on', 'this', 'moment', 'follow', 'this', 'feelingits', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'ways', 'its', 'alright', 'its', 'alright', 'its', 'alright', 'she', 'moves', 'in', 'mysterious', 'ways', 'ah', 'oh', 'oh', 'ah', 'huh', 'move', 'move', 'move', 'move', 'she', 'moves', 'with', 'it', 'she', 'moves', 'me', 'like', 'lift', 'my', 'days', 'and', 'light', 'up', 'my', 'nights', 'love']
# Nltk also provides for many different modules. Since there were no punctuations, I chose the stopwords module
from nltk.corpus import stopwords
nltk.download("stopwords")
[nltk_data] Downloading package stopwords to /Users/Helge/nltk_data...
[nltk_data]   Unzipping corpora/stopwords.zip.
True
# All the stopwords that were used, are retrieved by focussing on the set of stopwords.words
# Looking at the dataset, U2 uses a lot of stopwords, therefore filtering out the stopwords was the most logical step to take
stop_words = set(stopwords.words("english"))
print (stop_words)
set([u'all', u'just', u"don't", u'being', u'over', u'both', u'through', u'yourselves', u'its', u'before', u'o', u'don', u'hadn', u'herself', u'll', u'had', u'should', u'to', u'only', u'won', u'under', u'ours', u'has', u"should've", u"haven't", u'do', u'them', u'his', u'very', u"you've", u'they', u'not', u'during', u'now', u'him', u'nor', u"wasn't", u'd', u'did', u'didn', u'this', u'she', u'each', u'further', u"won't", u'where', u"mustn't", u"isn't", u'few', u'because', u"you'd", u'doing', u'some', u'hasn', u"hasn't", u'are', u'our', u'ourselves', u'out', u'what', u'for', u"needn't", u'below', u're', u'does', u"shouldn't", u'above', u'between', u'mustn', u't', u'be', u'we', u'who', u"mightn't", u"doesn't", u'were', u'here', u'shouldn', u'hers', u"aren't", u'by', u'on', u'about', u'couldn', u'of', u"wouldn't", u'against', u's', u'isn', u'or', u'own', u'into', u'yourself', u'down', u"hadn't", u'mightn', u"couldn't", u'wasn', u'your', u"you're", u'from', u'her', u'their', u'aren', u"it's", u'there', u'been', u'whom', u'too', u'wouldn', u'themselves', u'weren', u'was', u'until', u'more', u'himself', u'that', u"didn't", u'but', u"that'll", u'with', u'than', u'those', u'he', u'me', u'myself', u'ma', u"weren't", u'these', u'up', u'will', u'while', u'ain', u'can', u'theirs', u'my', u'and', u've', u'then', u'is', u'am', u'it', u'doesn', u'an', u'as', u'itself', u'at', u'have', u'in', u'any', u'if', u'again', u'no', u'when', u'same', u'how', u'other', u'which', u'you', u"shan't", u'shan', u'needn', u'haven', u'after', u'most', u'such', u'why', u'a', u'off', u'i', u'm', u'yours', u"you'll", u'so', u'y', u"she's", u'the', u'having', u'once'])
# Album_t is used as to retrieve the split_words that filters all the stop_words and leaves us with unique words
Split_words = Album_t

filtered_split_words = []

for w in Split_words:
    if w not in stop_words:
        filtered_split_words.append(w)
        
filtered_split_words
['heart',
 'bloom',
 'shoots',
 'stony',
 'ground',
 'theres',
 'room',
 'space',
 'rent',
 'townyoure',
 'luck',
 'reason',
 'care',
 'traffic',
 'stuck',
 'youre',
 'moving',
 'anywhereyou',
 'thought',
 'youd',
 'found',
 'friend',
 'take',
 'place',
 'someone',
 'could',
 'lend',
 'hand',
 'return',
 'graceits',
 'beautiful',
 'day',
 'sky',
 'falls',
 'feel',
 'like',
 'beautiful',
 'day',
 'dont',
 'let',
 'get',
 'awayyoure',
 'road',
 'youve',
 'got',
 'destination',
 'youre',
 'mud',
 'maze',
 'imaginationyoure',
 'lovin',
 'town',
 'even',
 'doesnt',
 'ring',
 'true',
 'youve',
 'youits',
 'beautiful',
 'day',
 'dont',
 'let',
 'get',
 'away',
 'beautiful',
 'daytouch',
 'take',
 'place',
 'teach',
 'know',
 'im',
 'hopeless',
 'casesee',
 'world',
 'green',
 'blue',
 'see',
 'china',
 'right',
 'front',
 'see',
 'canyons',
 'broken',
 'cloud',
 'see',
 'tuna',
 'fleets',
 'clearing',
 'sea',
 'see',
 'bedouin',
 'fires',
 'night',
 'see',
 'oil',
 'fields',
 'first',
 'light',
 'see',
 'bird',
 'leaf',
 'mouth',
 'flood',
 'colors',
 'came',
 'outit',
 'beautiful',
 'day',
 'dont',
 'let',
 'get',
 'away',
 'beautiful',
 'daytouch',
 'take',
 'place',
 'reach',
 'know',
 'im',
 'hopeless',
 'casewhat',
 'dont',
 'dont',
 'need',
 'dont',
 'know',
 'feel',
 'somehow',
 'dont',
 'dont',
 'need',
 'dont',
 'need',
 'beautiful',
 'dayis',
 'getting',
 'better',
 'feel',
 'make',
 'easier',
 'got',
 'someone',
 'blameyou',
 'say',
 'one',
 'love',
 'one',
 'life',
 'one',
 'need',
 'night',
 'one',
 'love',
 'get',
 'share',
 'leaves',
 'baby',
 'dont',
 'care',
 'itdid',
 'disappoint',
 'leave',
 'bad',
 'taste',
 'mouth',
 'act',
 'like',
 'never',
 'love',
 'want',
 'go',
 'withoutwell',
 'late',
 'tonight',
 'drag',
 'past',
 'light',
 'one',
 'get',
 'carry',
 'carry',
 'onehave',
 'come',
 'forgiveness',
 'come',
 'raise',
 'dead',
 'come',
 'play',
 'jesus',
 'lepers',
 'head',
 'ask',
 'much',
 'lot',
 'gave',
 'nothing',
 'got',
 'one',
 'hurt',
 'againyou',
 'say',
 'love',
 'temple',
 'love',
 'higher',
 'law',
 'love',
 'temple',
 'love',
 'higher',
 'law',
 'ask',
 'enter',
 'made',
 'crawl',
 'cant',
 'holding',
 'got',
 'got',
 'hurtone',
 'love',
 'one',
 'blood',
 'one',
 'life',
 'got',
 'shouldone',
 'life',
 'sisters',
 'brothersone',
 'life',
 'get',
 'carry',
 'carry',
 'otheroneoneyeah',
 'lover',
 'im',
 'streets',
 'gon',
 'na',
 'go',
 'bright',
 'lights',
 'big',
 'city',
 'meet',
 'red',
 'guitar',
 'fire',
 'desireshes',
 'candle',
 'burning',
 'room',
 'im',
 'like',
 'needle',
 'needle',
 'spoon',
 'counter',
 'shotgun',
 'pretty',
 'soon',
 'everybody',
 'got',
 'one',
 'fever',
 'im',
 'beside',
 'desire',
 'desiredesire',
 'desireburning',
 'burningyou',
 'dont',
 'know',
 'took',
 'know',
 'got',
 'oh',
 'lordy',
 'youve',
 'stealing',
 'thieves',
 'got',
 'caughtin',
 'headlights',
 'stretch',
 'car',
 'youre',
 'stardressing',
 'like',
 'sister',
 'living',
 'like',
 'tart',
 'dont',
 'know',
 'youre',
 'babe',
 'must',
 'artyoure',
 'headache',
 'suitcase',
 'youre',
 'staroh',
 'dont',
 'shy',
 'dont',
 'go',
 'blind',
 'hold',
 'thrill',
 'kiss',
 'kill',
 'meyou',
 'dont',
 'know',
 'got',
 'know',
 'want',
 'believing',
 'almost',
 'much',
 'doubtyoure',
 'big',
 'smash',
 'wear',
 'like',
 'rash',
 'staroh',
 'dont',
 'shy',
 'takes',
 'crowd',
 'cry',
 'hold',
 'thrill',
 'kiss',
 'kill',
 'methey',
 'want',
 'jesus',
 'theyll',
 'go',
 'one',
 'knee',
 'theyll',
 'want',
 'money',
 'back',
 'youre',
 'alive',
 'thirtythreeand',
 'youre',
 'turning',
 'tricks',
 'crucifix',
 'youre',
 'star',
 'oh',
 'childof',
 'course',
 'youre',
 'shy',
 'dont',
 'deny',
 'love',
 'hold',
 'thrill',
 'kiss',
 'kill',
 'mei',
 'climbed',
 'highest',
 'mountains',
 'run',
 'fields',
 'youi',
 'run',
 'crawled',
 'scaled',
 'city',
 'walls',
 'city',
 'walls',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'fori',
 'kissed',
 'honey',
 'lips',
 'felt',
 'healing',
 'fingertips',
 'burned',
 'like',
 'fire',
 'burning',
 'desire',
 'spoke',
 'tongue',
 'angels',
 'held',
 'hand',
 'devil',
 'warm',
 'night',
 'cold',
 'stone',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'fori',
 'believe',
 'kingdom',
 'come',
 'colors',
 'bleed',
 'one',
 'bleed',
 'one',
 'yes',
 'im',
 'still',
 'running',
 'broke',
 'bonds',
 'loosened',
 'chains',
 'carried',
 'cross',
 'shame',
 'oh',
 'shame',
 'know',
 'believe',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'fori',
 'climbed',
 'highest',
 'mountains',
 'run',
 'fields',
 'youi',
 'run',
 'crawled',
 'scaled',
 'city',
 'walls',
 'city',
 'walls',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'fori',
 'kissed',
 'honey',
 'lips',
 'felt',
 'healing',
 'fingertips',
 'burned',
 'like',
 'fire',
 'burning',
 'desire',
 'spoke',
 'tongue',
 'angels',
 'held',
 'hand',
 'devil',
 'warm',
 'night',
 'cold',
 'stone',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'fori',
 'believe',
 'kingdom',
 'come',
 'colors',
 'bleed',
 'one',
 'bleed',
 'one',
 'yes',
 'im',
 'still',
 'running',
 'broke',
 'bonds',
 'loosened',
 'chains',
 'carried',
 'cross',
 'shame',
 'oh',
 'shame',
 'know',
 'believe',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'still',
 'havent',
 'found',
 'im',
 'looking',
 'forsee',
 'stone',
 'set',
 'eyes',
 'see',
 'thorn',
 'twist',
 'side',
 'wait',
 'sleight',
 'hand',
 'twist',
 'fate',
 'bed',
 'nails',
 'makes',
 'wait',
 'wait',
 'without',
 'youwith',
 'without',
 'without',
 'youthrough',
 'storm',
 'reach',
 'shore',
 'give',
 'want',
 'im',
 'waiting',
 'youwith',
 'without',
 'without',
 'cant',
 'live',
 'without',
 'youand',
 'give',
 'away',
 'give',
 'away',
 'give',
 'give',
 'give',
 'awaymy',
 'hands',
 'tied',
 'body',
 'bruised',
 'shes',
 'got',
 'nothing',
 'win',
 'nothing',
 'left',
 'loseand',
 'give',
 'away',
 'give',
 'away',
 'give',
 'give',
 'give',
 'awaywith',
 'without',
 'without',
 'cant',
 'live',
 'without',
 'ohwith',
 'without',
 'without',
 'cant',
 'live',
 'without',
 'youwith',
 'without',
 'youjohnny',
 'take',
 'walk',
 'sister',
 'moon',
 'let',
 'pale',
 'light',
 'fill',
 'room',
 'youve',
 'living',
 'underground',
 'eating',
 'youve',
 'running',
 'away',
 'dont',
 'understand',
 'loveshes',
 'slippy',
 'youre',
 'sliding',
 'shell',
 'hit',
 'groundits',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'ways',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'waysjohnny',
 'take',
 'dive',
 'sister',
 'rain',
 'let',
 'talk',
 'things',
 'cant',
 'explain',
 'touch',
 'heal',
 'hurt',
 'steal',
 'want',
 'kiss',
 'sky',
 'better',
 'learn',
 'kneel',
 'knees',
 'boyshes',
 'wave',
 'turns',
 'tide',
 'sees',
 'man',
 'inside',
 'child',
 'yeahits',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'ways',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'ways',
 'alright',
 'alright',
 'alright',
 'lift',
 'days',
 'light',
 'nightsone',
 'day',
 'youll',
 'look',
 'back',
 'see',
 'held',
 'love',
 'could',
 'stand',
 'could',
 'move',
 'moment',
 'follow',
 'feelingits',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'ways',
 'alright',
 'alright',
 'alright',
 'moves',
 'mysterious',
 'ways',
 'ah',
 'oh',
 'oh',
 'ah',
 'huh',
 'move',
 'move',
 'move',
 'move',
 'moves',
 'moves',
 'like',
 'lift',
 'days',
 'light',
 'nights',
 'love']
Analysing song lyrics (40pts)
Consider the U2 songs in data/selected.

Use the NLP pipeline you have created in the previous section to answer the following questions:

What is the average length of a U2 song in number of words? What about the number of characters?
What are the most frequent words the band U2 uses in their lyrics (in this dataset)?
# The same directory is realized again to examine the numbers of U2 songs, here the length of the songs are determined with the function len
# As in the steps above, each song has been tagged with U2_number to create a new dictionary where l stands for length
U2_Songs = []
U2_Songs.extend([U2_1, U2_2, U2_3, U2_4, U2_5, U2_5, U2_6, U2_7])

new_dictionary = dict(zip(U2_list, U2_Songs))

U2_1_l = len(U2_1.split())
U2_2_l = len(U2_2.split())
U2_3_l = len(U2_3.split())
U2_4_l = len(U2_4.split())
U2_5_l = len(U2_5.split())
U2_6_l = len(U2_6.split())
U2_7_l = len(U2_7.split())

print(U2_1_l)
print(U2_2_l)
print(U2_3_l)
print(U2_4_l)
print(U2_5_l)
print(U2_6_l)
print(U2_7_l)

all_l = []
all_l.extend([U2_1_l, U2_2_l, U2_3_l, U2_4_l, U2_5_l, U2_6_l, U2_7_l])
264
243
59
178
186
169
239
# This shows the length of all the U2 songs individually
print(all_l)
# 264, 243, 59, 178, 186, 169, 239
[264, 243, 59, 178, 186, 169, 239]
# To add all these integers together, we get the total number of words all together by adding them up
total = sum(all_l)
print(sum(all_l))
# 1338
1338
# Since there are seven songs, the total will be divided by 7 as to retrieve the average
N_songs = 7
average = sum(all_l) // N_songs
print(average)
# 191
191
# To assess how many characters there are in each song we take each file and transform it into a string
# This showed for each song the number of characters, cha, that where detected in the string, str1
str1 = open("data/selected/beautiful_day.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("beautiful_day")        
print(cha)
        
str1 = open("data/selected/one.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("one")        
print(cha)

str1 = open("data/selected/desire.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("desire")        
print(cha)

str1 = open("data/selected/hold_me_thrill_me_kiss_me_kill_me.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("hold_me_thrill_me_kiss_me_kill_me")        
print(cha)

str1 = open("data/selected/i_still_havent_found_what_im_looking_for.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("i_still_havent_found_what_im_looking_for")        
print(cha)

str1 = open("data/selected/with_or_without_you.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("with_or_without_you")        
print(cha)

str1 = open("data/selected/mysterious_ways.txt").read()
cha = 0

for i in str1:
        cha = cha + 1
print("mysterious_ways")        
print(cha)

all_c = []

# beautiful_day 1299| one 1130| desire 324| hold_me_thrill_me_kiss_me_kill_me 876|i_still_havent_found_what_im_looking_for 915| with_or_without_you 838| mysterious_ways 1263
beautiful_day
1299
one
1130
desire
324
hold_me_thrill_me_kiss_me_kill_me
876
i_still_havent_found_what_im_looking_for
915
with_or_without_you
838
mysterious_ways
1263
# To examine the most popular words, the nltk.probability module is used to find the frequency of the tokenized data set of Album_t
# By making a new directory, U2, the .most_common() allowed to show the 50 most used words in order from most popular to less popular 
from nltk.probability import FreqDist

U2 = FreqDist(Album_t)
top_50 = U2.most_common(50)

print(top_50)
#[('you', 84), ('the', 72), ('i', 38), ('a', 37), ('to', 36), ('in', 29), ('and', 27), ('its', 25), ('it', 25), ('with', 24), ('me', 22), ('have', 22), ('but', 21), ('alright', 21), ('im', 20), ('what', 19), ('dont', 18), ('still', 14), ('one', 14), ('of', 14), ('or', 14), ('found', 13), ('without', 13), ('havent', 12), ('looking', 12), ('be', 12), ('love', 11), ('give', 11), ('got', 11), ('she', 11), ('for', 11), ('my', 10), ('youre', 10), ('know', 10), ('your', 10), ('like', 9), ('all', 8), ('this', 8), ('see', 8), ('moves', 8), ('on', 8), ('beautiful', 7), ('yourself', 7), ('away', 7), ('is', 7), ('not', 7), ('other', 7), ('mysterious', 6), ('want', 6), ('each', 6)]
[('you', 84), ('the', 72), ('i', 38), ('a', 37), ('to', 36), ('in', 29), ('and', 27), ('its', 25), ('it', 25), ('with', 24), ('me', 22), ('have', 22), ('but', 21), ('alright', 21), ('im', 20), ('what', 19), ('dont', 18), ('still', 14), ('one', 14), ('of', 14), ('or', 14), ('found', 13), ('without', 13), ('havent', 12), ('looking', 12), ('be', 12), ('love', 11), ('give', 11), ('got', 11), ('she', 11), ('for', 11), ('my', 10), ('youre', 10), ('know', 10), ('your', 10), ('like', 9), ('all', 8), ('this', 8), ('see', 8), ('moves', 8), ('on', 8), ('beautiful', 7), ('yourself', 7), ('away', 7), ('is', 7), ('not', 7), ('other', 7), ('mysterious', 6), ('want', 6), ('each', 6)]
Analysing more song lyrics (20pts)
Consider the full dataset of songs in data/all/billboard_lyrics_1964-2015.csv. This dataset contains 5100 lyrics. Please engage with the following question:

Who are the most popular artists or bands in this dataset?
It is recommended to use Pandas for this section.

from os import getcwd
os.getcwd()
'/Users/Helge/Desktop/CdH_exam_1'
# Unfortunately, I was not able to retrieve the directory and I could not find the billboard_lyrics
# I have tried everything, from changing files, to altering the file, to renaming it, etc
# But for some reason jupyter did not allow me to work with the data set
# Nevertheless, I was not able to work with the dataset, I hope that these last steps might give you an impression on what I wanted to achieve

# pandas enables datastructure and the manipulation of these structures
import pandas as pd

df = pd.read_csv("data/all/billboard_lyrics.csv")
# this contains the "Rank","Song","Artist","Year","Lyrics","Source"
print(df.colomns)

# We have 100 artists in this dataset, therefore the range is from 0 to 100
print(df["Artist"] [0:100])
print(df[["Rank", "Artist"]])

print(df.head(2))

# To assess who was in the top 5
df.loc[df["Rank"]] <= "5"
 dr.sort values("Name")
---------------------------------------------------------------------------
IOError                                   Traceback (most recent call last)
<ipython-input-145-dc968fdcfcce> in <module>()
      4 import pandas as pd
      5 
----> 6 df = pd.read_csv("billboard_lyrics")
      7 # this contains the "Rank","Song","Artist","Year","Lyrics","Source"
      8 print(df.colomns)

/opt/anaconda2/lib/python2.7/site-packages/pandas/io/parsers.pyc in parser_f(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, skipfooter, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, doublequote, escapechar, comment, encoding, dialect, tupleize_cols, error_bad_lines, warn_bad_lines, delim_whitespace, low_memory, memory_map, float_precision)
    700                     skip_blank_lines=skip_blank_lines)
    701 
--> 702         return _read(filepath_or_buffer, kwds)
    703 
    704     parser_f.__name__ = name

/opt/anaconda2/lib/python2.7/site-packages/pandas/io/parsers.pyc in _read(filepath_or_buffer, kwds)
    427 
    428     # Create the parser.
--> 429     parser = TextFileReader(filepath_or_buffer, **kwds)
    430 
    431     if chunksize or iterator:

/opt/anaconda2/lib/python2.7/site-packages/pandas/io/parsers.pyc in __init__(self, f, engine, **kwds)
    893             self.options['has_index_names'] = kwds['has_index_names']
    894 
--> 895         self._make_engine(self.engine)
    896 
    897     def close(self):

/opt/anaconda2/lib/python2.7/site-packages/pandas/io/parsers.pyc in _make_engine(self, engine)
   1120     def _make_engine(self, engine='c'):
   1121         if engine == 'c':
-> 1122             self._engine = CParserWrapper(self.f, **self.options)
   1123         else:
   1124             if engine == 'python':

/opt/anaconda2/lib/python2.7/site-packages/pandas/io/parsers.pyc in __init__(self, src, **kwds)
   1851         kwds['usecols'] = self.usecols
   1852 
-> 1853         self._reader = parsers.TextReader(src, **kwds)
   1854         self.unnamed_cols = self._reader.unnamed_cols
   1855 

pandas/_libs/parsers.pyx in pandas._libs.parsers.TextReader.__cinit__()

pandas/_libs/parsers.pyx in pandas._libs.parsers.TextReader._setup_parser_source()

IOError: [Errno 2] File billboard_lyrics does not exist: 'billboard_lyrics'

#!usr/bin/env/python
# -*- coding: latin-1 -*-
import re

# Beware of clbuttic errors!
# http://thedailywtf.com/Articles/The-Clbuttic-Mistake-.aspx

# Clbuttics errors are named this way because they happen when a badword filter
# may easily think that "Charles Dickens" is a bad word, because of "Dick".

# I tried to fix partially those by removing small bad words from the list.
# Still, pay attention to this.

class WordParser:

    # A char will match with all the other chars in his string.
    bank = ['3 f e é è ë ê', '0 o ô ò ö', '1 i l ì î ï | !',
            '@ a à â ä', '$ s z', 'c ç k']
    regexes = []

    def __init__(self, file="badwords.txt"):
        self.wordlist = open(file).read().split('\n')
        
        for i in self.wordlist:
            if not i.isalpha(): continue
            if len(i) > 3:
                self.regexes.append(self.format_word(i))
                print i

   


    def format_word(self, word):
        
        # This function will format a badword and return a compiled regex.
        result = ""

        
        for i in range(len(word)):

            pattern = word[i]

            for letterpattern in self.bank:
                if word[i] in letterpattern:
                    pattern = letterpattern

            toadd = '['+pattern+']+'

            if i == len(word)-1:
                result+=toadd
                continue
                
            if word[i+1] == word[i]:

                continue
            
            result+=toadd

        return (result, word)


    def browse_re(self, word):
        # Look in a list of bad words.
        # Combined letter to vowel and regexp makes it very powerful.
        word = word.lower()
        

        for reg in self.regexes:
            if reg[0] == '': # There is always an empty tuple at the end.
                continue
            
            if type(re.search(reg[0], str(word))) != type(None):
                yield reg[1]


BadWords = WordParser()




                    
            
        


        
            

        

        
        

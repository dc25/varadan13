---
layout: post
theme: 

categories: Jupyter_Notebooks
---

strip() method  

Remove spaces at the beginning and at the end of the string  
The strip() method removes any leading (spaces at the beginning) and trailing (spaces at the end) **characters** (space is the default leading character to remove)  

    		#EXAMPLE 1
            
            txt = "     banana     "

    		x = txt.strip() ## here the trailing and beginning white space is removed 
            
            #EXAMPLE 2 
            
            txt = ",,,,,rrttgg.....banana....rrr"

    		x = txt.strip(",.grt") ## here trailing and beginning characters like , . g r t are removed 
            
            #OUTPUT
            
            "banana"

Split()  

Split a string into a list where each word is a list item    

INPUT PARAMETERS  
separator--Optional. Specifies the separator to use when splitting the string. By default any whitespace is a separator  
maxsplit--Optional. Specifies how many splits to do. Default value is -1, which is "all occurrences"

       		#EXAMPLE 1
            
            txt = "welcome to the jungle"

    		x = txt.split() # HERE TXT WHICH IS STRING IS CONVERTED INTO LIST 
            
            ## OUTPUT 
            
            ['welcome', 'to', 'the' , 'jungle']
            
            #EXAMPLE 2 
            
            txt = "hello, my name is Peter, I am 26 years old"

    		x = txt.split(", ")
            
            ## OUTPUT
            
            ['hello','my name is Peter', 'I am 26 years old']
            
            #EXAMPLE 3 
            
            txt = 'hell#hi"
            
            x = txt.split('#')
            
            ## OUTPUT 
            
            ['hell','hi']
            

map()

map(function, iterables) 

    		def myfunc(a, b):

  			return a + b

    		x = map(myfunc, ('apple', 'banana', 'cherry'), ('orange', 'lemon', 'pineapple')) 

re.escape()

re.finditer()

re.compile()

re.

class My_class(object):  
…”object” is a kind of placeholder, letting Python know you don’t want to inherit the properties of some other class. You’re making a class with the very basic rules, and your code will set up everything else.  
In the exercises the Triangle class inherits the more generic Shape class, like this:   
{% highlight python linenos %}
class Triangle( Shape ):  
But sometimes you are writing a class and you don’t want or need to inherit from another class. In this case, you fill in object, which is referring to a very basic, generic class that makes plain old “objects”.

    		class Rectangle:

                    def __init__(self, length, breadth, unit_cost=0):
       						self.length = length
       						self.breadth = breadth
       						self.unit_cost = unit_cost

                     def get_area(self):
       						return self.length * self.breadth

                     def calculate_cost(self):
       						area = self.get_area()
      					 	return area * self.unit_cost
    		
            # breadth = 120 units, length = 160 units, 1 sq unit cost = Rs 2000
    		
            r = Rectangle(160, 120, 2000)
    		print("Area of Rectangle: %s sq units" % (r.get_area()))
{% endhighlight %}
###

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## 1. Required evidence

### 1.1. Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### 1.2. Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

![Sample](screenshots/sample.png)
> Note the `!`, and the use of a relative path.

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### 1.3. Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### 1.4. Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## 2. Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### 2.1. Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/screenshot_2-1-4-a.png)

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/screenshot_2-1-4-b.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### 2.2. Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name   | value       |
   | ----------              |--------|-------------|
   | built-in primitive type | dimmed | True        |
   | built-in composite type | GREEN  | (0, 255, 0) |
   | user-defined type       | Smiley | N/A         |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type   |
   | ------------             |--------|
   | self.pixels              | list   |
   | A member of self.pixels  | tuple  |
   | self                     | Smiley |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File     | First line | Line range |
   | ------------ |----------| -------- |------------|
   |  sequence    | happy.py | self.draw_eyes(wide_open=False)         | 39-43      |
   |  selection   | sad.py   | if wide_open:         | 26-30      |
   |  iteration   | sad.py   | for pixel in eyes:         | 25-30      |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example               |
   | ----------------------- |-------|-----------------------|
   | int                     | y     | RED = (255, 0, 0)                      |
   | float                   | y     | delay=0.25                      |
   | str                     | n     | error = "nose not found" |
   | bool                    | y     | wide_open=True        |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> A class variable:
> `WHITE = (255, 255, 255)`
> An instance variable:
> `self.sense_hat = SenseHat()`
> A class variable is shared by all instances of the class and defined in the body of the class before any methods.
> An instance variable is defined in the __init__ method and are attached to the self.
>

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > A constructor passes information to each new instance. 
   > This constructor calls the `__init__` method variables inherited from the `Smiley` class as well as 
   > `draw_mouth()` and `draw_eyes()` methods. (`Blinkable` does not have an `__init__` method currently.)
   >

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > `super().__init__()`
   > `self.draw_mouth()`
   > `self.draw_eyes()`
   > `self.sense_hat = SenseHat()`
   > `Y = self.YELLOW`
   > `O = self.BLANK`
   > `self.pixels = [...]`
   > 
   > The result: renders a happy face in SenseHat.

### 2.3. Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:

> PEP8. It is likely to be the same style as used in the SenseHat, by looking at the formatting of the methods and 
> attributes being called from that class.
>

2. List three aspects of this convention you see applied in the code.

> 1. `self.sense_hat = SenseHat()` camel case for the class name
> 2. `self.sense_hat.set_pixels(self.pixels)` snake case for the method name
> 3. `mouth = [41, 46, 50, 51, 52, 53]` single spaces between the values.
>

3. Give two examples of organizational documentation in the code.

> 1. `# We have encapsulated the SenseHat object`
> 2. `        """
        Set the SenseHat's light intensity to low (True) or high (False)
        :param dimmed: Dim the display if True, otherwise don't dim
        """`
>

### 2.4. Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s)  |
|------------|---------------|-------------------|
| Smiley     | Super         | object            |
| Blinkable  | Sub           | ABC               |
| Sad        | Sub           | Smiley            |
| Happy      | Sub           | Smiley, Blinkable |


2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction: can apply to a class, or a method. An abstract class is a blueprint for other classes and cannot be 
> instantiated. Abstract methods do not have concrete implementation. 
> Example: 
> ```
>     @abstractmethod
>     def blink(self):
>         pass
> ```
>

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> Inheritance. In this project inheritance is used to manipulate a template to display different expressions with 
> the option of an animated blink behavior. 
>

### 2.5. Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > The `mouth` variable has different values
   >
2. What are the key similarities?
   > They both have `draw_mouth` and `draw_eyes` methods
   >
3. What difference stands out the most to you and why?
   > `Happy` inherits from the `Blinkable` class, `Sad` does not.
   >
4. How does this difference affect the functionality of these classes
   > `Happy` has to have a function to make the `SenseHat` 'blink', `Sad` does not.
   >

### 2.6. Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > Smiley, Happy, Sad
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > Smiley
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > By encapsulating SenseHAT data and methods within a class `SenseHat` in a separate module `sense_hat`, those 
   > elements are hidden from view. This prevents accidental or intentional editing of the code from outside the module 
   > and helps to simplify code maintenance. 
   > Elements of SenseHAT can be called from outside the module: the `sense_hat.low_light` property and 
   > `sense_hat.set_pixels()` method from `SenseHat` have been accessed in the Smiley class.
   > Modifying and using these in the `Smiley` class would not impact the reusability of `SenseHat` in 
   > other parts of the code. In this program, `Smiley` is the only class that contains direct references to SenseHAT; 
   > other modules can import from `Smiley` to execute SenseHAT code without knowing SenseHAT exists.  
   >

### 2.7. Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> The author does not believe that every `Smiley` should be able to blink, as they have put the `blink` method in a 
> separate class that is not referenced in `Smiley`.
>

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> The smileys that blink, currently, are only `Happy`. The author does not expect all instances of this class to blink in the same 
> way as each instance can specify the value of `delay` within the blink method. 
> If other smileys are to blink, the 
> author does not expect them to blink in the same way; `blink` does not have an implementation in the `Blinkable` class, only 
> an abstract method that returns `pass`; leaving it open for each smiley type to be coded to blink differently.
> 

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism is when objects have a comparable shape that can take many forms. In reference to `blink`: 
> The Happy class claims to be blinkable and is an example of subclass polymorphism. It contains the `blink` method 
> inherited from `Blinkable`. Conversely, the Sad Smiley class does not reference the `Blinkable` class or contain a 
> `blink` method.
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> The blink method is an abstract method, that is inherited by and can be defined in the subclass. Here, `Happy` has to have a 
> blink method because it is a subclass of `Blinkable`, but can define the specific behaviour of that method to suit 
> itself, making it an example of polymorphism.
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
       pass  # Replace 'pass' with your implementation
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![Sad Smiley Blinking](screenshots/Screenshot_2-7-x-3.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > You have to make sure to import the `Sad` class into `main.py`.

  ### 2.8. If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

   > Abstract Base Class

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > Interface

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Abstraction. `Blinkable` contains an abstract method (a method without concrete implementation), that will have to 
  > be defined by any instantiated child classes that inherit from `Blinkable`; the `Blinkable` class defines a contract 
  > for those classes. This interface simplification is a key concept of abstraction. 
  > 

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > I could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation without directly using Blinkable 
  > because nothing in the Blinkable class references or contains code that cannot also be defined in or called directly from the Sad class.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > This is known as duck typing - 
  > you do not need to know the class/type of the object in order to call a method, as long as the object has it.
  > This works in Python and most dynamically typed languages because unlike static languages (C#), they will respond
  > by using context to run the code, without first verifying if the object is a specific type.
  > 

  ***

  ## 3. Refactoring

  ### 3.1. Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > White, green, red, yellow, and blank, are defined in the Smiley class (and inherited by its subclasses)
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > Tuples. No, the values are not expected to change - if the values within the tuple change, they are not longer accurate to the variable's name. (Not the colour described.)
     3. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > Smiley, Happy, Sad.

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > Change the first value in the YELLOW tuple to `0`. (Chaotic idea though.)

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### 3.2. Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### 3.3. Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](screenshots/Screenshot_3-3-iv.png)
  ![Bulk Rename](screenshots/Screenshot_3-3-iv-b.png)
- 
  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### 3.4. Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***

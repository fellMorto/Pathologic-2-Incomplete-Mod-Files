# Speech.xml
Block designating a dialog said by a character

Each Speech references Replies, Entrypoint, the Text being said, and Graphlinks. The **AuthorGUID** and **Owner** are the ID of the character speaking, from Character.xml. The **Parent** is the Talking graph the Speech is contained within.

![image](https://github.com/user-attachments/assets/c99812af-a277-4e2e-bca3-63811e58d539)

# Entry.xml
Entrypoint attached to a Speech. It can be used to attach an Action to the Speech.

![image](https://github.com/user-attachments/assets/edd4c9e7-b04d-4e92-b2ae-e804238e4ac5)


# Reply.xml
The Replies to choose from, under each Speech text. Each Reply references the Text being said, and has an **OrderIndex** for each Reply. (I'm not sure what the other conditions do). The **Parent** is the Speech it's attached under.

![image](https://github.com/user-attachments/assets/4974fa9f-ced9-4be6-8ddc-bde41ae269e4)


# Graphlink.xml
Links determining which Speech to go to, from each Reply. Each Reply gets its own Graphlink.

Each Graphlink references the source Speech it's coming from, and which next Speech it's going to. Each Graphlink also has its own **SourceExitPointIndex.** Each Reply gets its own associated Graphlink, so the replies can lead to different Speech. The **Parent** is the Talking graph.

![image](https://github.com/user-attachments/assets/9d945887-1d14-4620-94ca-f310c1fd245d)

If the Reply ends the conversation, just remove the **Destination** from the Graphlink. Then it will exit the conversation.

![image](https://github.com/user-attachments/assets/9331cbaf-6580-4380-aba8-717099964084)



# English.txt
Document containing the text referenced for dialog

![image](https://github.com/user-attachments/assets/f4dba858-56ab-4399-906b-fd873136dcdd)


# Branch
Branch = a way to navigate to different Speech, based on Conditions. Each Talk has a starting Branch, so you can navigate to different initial Speeches at the start of the conversation.

Each branch has an entrypoint, and can have multiple Outputlinks which it goes to based on Branch Conditions. Its Parent is the **Talking** graph.

For this example, I have a Condition set. If the Condition is met, it will navigate to the first Outputlink and the Speech I want. Otherwise, it navigates to the second Outputlink. There can be multiple Conditions.

![image](https://github.com/user-attachments/assets/9c3127ff-81d4-4375-9f8a-09c0aa9e4092)

There are other types of Conditions the Branch can use. Branch Type **STATE_TYPE_MAXVALUE_BRANCH** will look for the Condition with the largest value (I think?). I saw these branches used to set a -1 generic state, and navigate to other states by raising a value to 1 for example.

If you don't have any conditions for the starting Speech, just have a generic Branch with one Outputlink to the first Speech.

![image](https://github.com/user-attachments/assets/be49b138-f7d1-4995-aaac-c54fd60808e9)

# To add conditions and actions
Replies can have a Condition, and set an Actionline. The Reply will only appear if the Condition is met, and it will perform the Actions if it's selected.

![image](https://github.com/user-attachments/assets/aa6b5582-0aa3-4791-9010-40fbe17af214)

Entrypoints can also set an Actionline for a Speech.

![image](https://github.com/user-attachments/assets/9923e3d0-929a-4976-b85a-2105f7ed67ca)


# Talking.xml

Block designating all the Speech and Graphlinks in a conversation. It also includes the initial talking Branch and any other Branches in the conversation. Each Talk also has an Entrypoint. Its **Owner** is the Character it's attached to, and its **Parent** is the Event Graph for that character. Add any new Talking to this Character Event Graph.

![image](https://github.com/user-attachments/assets/c92fa664-9bfe-485c-b9be-d2dacd6b4995)


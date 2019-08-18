# தமிழில் கற்போம் கிட்ஹப்(GitHub) 

கணினி மென்பொருள் நிரலாக்கத்துறையில் முதன் முதலில் ஏதேனும் கற்கும்பொழுது `ஹலோ வேர்ல்ட்` என்று சொல்லி தொடங்குவது மரபாகும். நாமும் மரபின் வழி கிட்ஹப் தளத்தைப் பற்றி கற்க தொடங்குவோம்.

இங்கே நீங்கள் கீழ்கண்டவற்றை கற்பீர்கள்:

- களஞ்சியங்களை உருவாக்க மற்றும் பயன்படுத்த 
- கிளைகளை தொடங்க மற்றும் நிர்வகிக்க 
- கோப்புகளை மாற்றம் செய்து அவற்றை கிட்ஹப்பில் ஒப்படைக்க
- இழுவை கோரிக்கைகளை உருவாக்க மற்றும் சேர்க்க

## கிட்ஹப் என்றால் என்ன?
கிட்ஹப் என்பது நிரல் கோப்புகளை பதிப்பு கட்டுப்பாடு செய்வதற்கும் நிரல் கோப்புகள் மீது உடனுழைப்பு செய்வதற்கும் நிரல் கோப்புகளை சேமித்து வைக்கும் தளமாகும். உலகின் எம்மூலையில் இருப்போரோடும் ஒரு திட்டத்தில் உடனுழைப்பு செய்ய இத்தளம் உதவுகிறது.

இங்கே நீங்கள் களஞ்சியங்கள், கிளைகள், ஒப்படைப்புகள், இழுவை கோரிக்கைகள் போன்ற கிட்ஹப்பின் அடிப்படைகளைப் பற்றி அறியலாம். நீங்கள் "Hello World" என்றொரு களஞ்சியத்தை உருவாக்குவீர்கள். அக்களஞ்சியத்தில் இழுவை கோரிக்கை ஒன்றை உருவாக்கி நீங்கள் செய்த மாற்றங்களை மறுசீராய்வு செய்வீர்கள்.

### நிரலாக்கம் தேவையில்லை
இப்பயிற்சியை நிறைவு செய்ய இணைய இணைப்பும் ஒரு கிட்ஹப் கணக்கும் போதுமானது. நிரலாக்கம் செய்ய தெரிந்திருக்க வேண்டும் என்று அவசியம் இல்லை.

> துணுக்கு: இப்பக்கத்தை வேறொரு உலாவி சாளரத்தில் திறந்து கொள்ளவும். இவ்வாறு செய்வதன் மூலம் நீங்கள் இப்பக்கத்தை பார்த்துக்கொண்டே கீழ் சொல்லப்பட்டிருக்கும் பயிற்சிகளை செய்ய இயலும்.

## முதற்படி - களஞ்சியத்தை உருவாக்குக
ஒரு களஞ்சியம் என்பது பொதுவாக இரு திட்டத்தை ஒழுங்கமைக்க பயன்படுத்தப்படுகிறது. நீங்கள் உங்கள் களஞ்சியத்தில் அடைவைகள், கோப்புகள், படங்கள், காணொளிகள் மாறும் இதர தகவல்களையும் சேர்த்து வைக்க முடியும். நீங்கள் நிர்வகிக்கும் திட்டத்தைப்பற்றி விளக்க README எனும் கோப்பை உங்கள் களஞ்சியத்துடன் இணைக்க கிட்ஹப் பரிந்துரைக்கிறது.

உங்கள் சிந்தனைகளையும் எண்முறை வளங்களையும் சேமிக்கவும் பகிரவும் களஞ்சியங்களை பயன்படுத்தலாம். உங்கள் திட்டத்தின் மீதான விவாதங்களையும் இக்களஞ்சியத்தின் மீது நடத்தலாம். இப்பொழுது "hello world" என்றொரு களஞ்சியத்தை உருவாக்கி மேற்கூறியவற்றை எவ்வாறு செய்வது என்று பாப்போம்.

### புதிய களஞ்சியத்தை உருவாக்க
- கிட்ஹப் பக்கத்தின் மேல்புறம் வலது மூலையில் சிறுபடம் ஒன்றிருக்கும். அதனருகில் இருக்கும் *+* குறியீட்டை அழுத்தவும். அதன் பின்பு `New Repository` என்பதை அழுத்தவும்.  
- `hello-world` என்று பெயரிடவும்
- சிறுகுறிப்பு எழுதவும்
- `Initialize this repository with a README` என்பதை தேர்வு செய்யவும்.
- `Create repository` என்பதை அழுத்தவும் 



Step 2. Create a Branch
Branching is the way to work on different versions of a repository at one time.

By default your repository has one branch named master which is considered to be the definitive branch. We use branches to experiment and make edits before committing them to master.

When you create a branch off the master branch, you’re making a copy, or snapshot, of master as it was at that point in time. If someone else made changes to the master branch while you were working on your branch, you could pull in those updates.

This diagram shows:

The master branch
A new branch called feature (because we’re doing ‘feature work’ on this branch)
The journey that feature takes before it’s merged into master
a branch

Have you ever saved different versions of a file? Something like:

story.txt
story-joe-edit.txt
story-joe-edit-reviewed.txt
Branches accomplish similar goals in GitHub repositories.

Here at GitHub, our developers, writers, and designers use branches for keeping bug fixes and feature work separate from our master (production) branch. When a change is ready, they merge their branch into master.

To create a new branch
Go to your new repository hello-world.
Click the drop down at the top of the file list that says branch: master.
Type a branch name, readme-edits, into the new branch text box.
Select the blue Create branch box or hit “Enter” on your keyboard.
branch gif

Now you have two branches, master and readme-edits. They look exactly the same, but not for long! Next we’ll add our changes to the new branch.


Step 3. Make and commit changes
Bravo! Now, you’re on the code view for your readme-edits branch, which is a copy of master. Let’s make some edits.

On GitHub, saved changes are called commits. Each commit has an associated commit message, which is a description explaining why a particular change was made. Commit messages capture the history of your changes, so other contributors can understand what you’ve done and why.

Make and commit changes
Click the README.md file.
Click the  pencil icon in the upper right corner of the file view to edit.
In the editor, write a bit about yourself.
Write a commit message that describes your changes.
Click Commit changes button.
commit

These changes will be made to just the README file on your readme-edits branch, so now this branch contains content that’s different from master.


Step 4. Open a Pull Request
Nice edits! Now that you have changes in a branch off of master, you can open a pull request.

Pull Requests are the heart of collaboration on GitHub. When you open a pull request, you’re proposing your changes and requesting that someone review and pull in your contribution and merge them into their branch. Pull requests show diffs, or differences, of the content from both branches. The changes, additions, and subtractions are shown in green and red.

As soon as you make a commit, you can open a pull request and start a discussion, even before the code is finished.

By using GitHub’s @mention system in your pull request message, you can ask for feedback from specific people or teams, whether they’re down the hall or 10 time zones away.

You can even open pull requests in your own repository and merge them yourself. It’s a great way to learn the GitHub flow before working on larger projects.

Open a Pull Request for changes to the README
Click on the image for a larger version

Step	Screenshot
Click the  Pull Request tab, then from the Pull Request page, click the green New pull request button.	pr-tab
In the Example Comparisons box, select the branch you made, readme-edits, to compare with master (the original).	branch
Look over your changes in the diffs on the Compare page, make sure they’re what you want to submit.	diff
When you’re satisfied that these are the changes you want to submit, click the big green Create Pull Request button.	create-pull
Give your pull request a title and write a brief description of your changes.	pr-form
When you’re done with your message, click Create pull request!

Tip: You can use emoji and drag and drop images and gifs onto comments and Pull Requests.


Step 5. Merge your Pull Request
In this final step, it’s time to bring your changes together – merging your readme-edits branch into the master branch.

Click the green Merge pull request button to merge the changes into master.
Click Confirm merge.
Go ahead and delete the branch, since its changes have been incorporated, with the Delete branch button in the purple box.
merge delete

Celebrate!
By completing this tutorial, you’ve learned to create a project and make a pull request on GitHub!

Here’s what you accomplished in this tutorial:

Created an open source repository
Started and managed a new branch
Changed a file and committed those changes to GitHub
Opened and merged a Pull Request
Take a look at your GitHub profile and you’ll see your new contribution squares!

To learn more about the power of Pull Requests, we recommend reading the GitHub flow Guide. You might also visit GitHub Explore and get involved in an Open Source project.

Tip: Check out our other Guides, YouTube Channel and On-Demand Training for more on how to get started with GitHub.

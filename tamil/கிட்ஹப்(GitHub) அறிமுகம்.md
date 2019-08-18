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

<img src="createrepo.png" height="400" width="400"/>

## இரண்டாம் படி - கிளையை உருவாக்குக
ஒரு களஞ்சியத்தின் வெவ்வேறு பதிப்புகளின் மீது பங்களிப்பாற்ற  கிளைகள் உதவுகின்றன. ஒரு களஞ்சியத்தின் ஒவ்வொரு கிளையும் ஒவ்வொரு பதிப்பாகும். 

வழக்கமாக நாம் உருவாக்கும் களஞ்சியத்தில் `master` எனும் ஒரு கிளை மட்டுமே இருக்கும். இக்கிளையே உங்கள் களஞ்சியத்தின் உறுதியான பாதிப்பாகும். நீங்கள் இக்கிளையில் ஏதேனும் மாற்றங்கள் செய்ய நினைத்தால் அதை நேரிடையாக செய்யாது இன்னொரு கிளையில் செய்வது வழக்கமாகும்.

ஒரு புதிய கிளையை ஏற்கனவே இருக்கும் ஒரு கிளையில் இருந்தே உருவாக்க முடியும். இப்பொழுது நாம் `master` கிளையில் இருந்து இன்னொரு கிளையை உருவாக்குவோம்.

### புதிய கிளையை உருவாக்க 
- நீங்கள் உருவாக்கிய `hello-world` எனும் களஞ்சியத்திற்கு செல்லவும்
- `branch : மாஸ்டர்` எனும் கீழ்விழும் பட்டியலை அழுத்தவும் 
- கீழ்விழும் பட்டியல் வந்தவுடன் அதிலிருக்கும் எழுத்துப்பெட்டியில் தங்களது புதிய கிளையின் பெயரை `feature` என உள்ளிடவும்.
- பின்பு `create branch` என்பதனை அழுத்தவும்.   

<img src="newbranch.PNG" height="250" width="250"/>

இப்பொழுது உங்கள் களஞ்சியத்தில் இரண்டு கிளைகள் உள்ளன. ஒன்று `master`. இன்னொன்று `feature`. மேற்கூறிய இரு கிளைகளும் ஒன்றுபோல் வேற்றுமையின்றி இருக்கும். மூன்றாம் படியில் நாம் புதிதாக உருவாக்கிய கிளையில் சிறு மாற்றங்களை செய்வோம்.  

## மூன்றாம் படி - மாற்றம் செய்து ஒப்படைத்தல்
இப்பொழுது நீங்கள் `feature` எனும் கிளையில் உள்ளீர்கள். இந்த கிளைக்கும் `master` கிளைக்கும் இதுவரை எவ்வேறுபாடும் இல்லை. நாம் இப்பொழுது  `feature` கிளையில் சிறு மாற்றங்கள் செய்வோம்.

கிட்ஹப்பில் நாம் செய்த மாற்றங்களை சேமிக்க 'ஒப்படைத்தல்' எனும் செயலை செய்ய வேண்டும். ஒவ்வொரு ஒப்படைப்பிற்கும் ஒரு ஒப்படைத்தல் செய்தியை வழங்க வேண்டும். இந்த ஒப்படைத்தல் செய்தியானது நாம் செய்த மாற்றத்தை பிறர் புரிந்துகொள்ள உதவும்.

### மாற்றம் செய்து ஒப்படைத்தல் 
- `README.md` எனும் கோப்பை அழுத்தவும்
- பக்கத்தின் மேல் புறத்தில் இருக்கும் கரிக்கோல் உருவத்தை அழுத்தவும்
- எழுதியில் உங்களைப்பற்றி சிறிது எழுதவும் 
- நீங்கள் செய்த மாற்றத்தை விளக்கும் வகையில் ஒப்படைப்பு செய்தியை  `Commit Changes` என்ற எழுத்துப்பெட்டியில் உள்ளிடவும்
- `Commit Changes` எனும் பொத்தானை  அழுத்தவும்

நீங்கள் மேலே கூறியது போல செய்த மாற்றங்கள் `feature` கிளையில் உள்ள README கோப்பில் மட்டுமே இருக்கும். `master` கிளையிலுள்ள README கோப்பில் இம்மாற்றங்கள் இராது. இப்பொழுது உங்கள் `feature` கிளையானது `master` கிளையில் இருந்து வேறுபட்டிருக்கிறது.

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

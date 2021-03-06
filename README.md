# pollsapi

- Create content for index page
    - "Write your first view" 
    - Assumes polls.urls exist
    - Assumes mysite.urls has proper include for polls.urls

- Create question
    - POST /api/polls/questions/

- List questions
    - GET /api/polls/questions/
    - Only shows the question text and date published

- List questions with was_published_recently
    - /api/polls/questions/
    - Change serializer

- List questions with filtering.
    - Question starts with 'What'
    - /api/polls/questions/?text=What&filter=starts__with

- Create choice for a particular question
    - /api/polls/questions/<pk>/choices/

- Detail question
    - GET /api/polls/questions/<pk>/
    - List all the available choices for the question

- Vote for a particular choice on a particular question
    - /api/polls/questions/<pk>/vote
        - questions.choice_set.get(id=request.POST['choice'])
        - Return descriptive message if choice is missing, or if choice doesn't point to correct id.
        - Fix with serializers
    - /api/polls/questions/<pk>/choices/<pk>/vote/

- Question voting results
    - GET /api/polls/questions/<pk>/results
    - Choices with number of votes for each question
    - Show how we can have ChoiceSerializer and ChoiceWithVotesSerializer by extending ChoiceSerializer

- Edit question
    - /api/polls/questions/<pk>/
    - PUT or PATCH?

You should know basic math before you start using a calculator. 

Generic view for list (GET /api/polls/questions/) and detail (GET /api/polls/questions/<pk>)

### Optional

- All choices for a particular question
    - /api/polls/questions/<pk>/choices/

- Edit choice
    - /api/polls/choices/<pk>/

- Creating multiple questions 

- Creating multiple choices for a question

- Creating multiple questions along with multiple choices.

- List of all users
    - Without password

- Create user (signup)
- Login

- Authentication

- Generic api views
    - TemplateView
    - ListView
        - pagination
    - CreateView
    - UpdateView


- Using DRF generic views


- Testing the apis
- Using kwargs partial on serializer
- Using kwargs context on serializer
- Using kwargs allow_empty with many on serializer
- ModelSerializer.save(user=request.user) could be used
- Can serializer.validated_data be edited and we can do serializer.validated_data['user'] = request.user before calling serializer.save().
- raise_exception with is_valid()
- Add a custom validation on a particular serializer field. Add validation_question_text().
- Add validator kwarg to Field
- source * and source abc.def
- is_valid() must be called before calling save().
- Show usage of source. Use question = serializers.CharField(max_length=100, source='question_text')
- Show usage of source=user.email on BookSerializer.user_email.
    - BookSerializer
        - user_email = serializers.EmailField(read_only=True, source='user.email')
- Show usage of source='*'
question = serializers.CharField(max_length=200, read_only=True, source='question_text')

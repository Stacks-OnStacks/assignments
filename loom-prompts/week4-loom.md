# AWS, DevOps, Hibernate

# REMINDER: Each prompt is answerable in 5min. You must record your screen as well with this prompt on the foreground.

[Here is the link for the survey to be completed after.](https://forms.office.com/r/2ty04ksdbs)

# Prompt 1

1. What is AWS? Why would we use it?

2. Name a few AWS services and what they do.

3. What is AWS S3?

4. What is Continuous Integration & Continuous Deployment? Why use it?

5. What is AWS CodePipeline?

# Prompt 2

1. What can you tell me about the Stream API?

2. What is a lambda expresion in java?

3. What is an ORM?

4. What is JPA annotations? What are the most commonly used ones and what do they do?

5. What configuration is required in order to use Hibernate in our project?

# Prompt 3

Explain the following code. Line-by-line. **_NOTE_** Answer some of the comments.

```java

    // Explain the statements executed from the following two methods:

    // Method 1:
    public List<MemberResponse> readAll(){

        // Explain what is happening below for each method being invoked?
        List<MemberResponse> members = memberDao.findAll() // findAll method =
                                                .stream() // stream method =
                                                .map(MemberResponse::new) // map method =
                                                .collect(Collectors.toList());// collect method =
        ;
        return members;
    }

    //Method 2
    public boolean update(EditMemberRequest editMember) throws InvalidUserInputException{

        Member foundMember = memberDao.findById(editMember.getId()); // why make this DAO call?

        // What is a Predicate?
        // What's -> handling for us?
        Predicate<String> notNullOrEmpty = (str) -> str != null && !str.trim().equals("");


        // What's going on with these if statements?
        if(notNullOrEmpty.test(editMember.getFullName())){
           foundMember.setFullName(editMember.getFullName());
        }
        if(notNullOrEmpty.test(editMember.getPassword())){
               foundMember.setPassword(editMember.getPassword());
        }
        if(notNullOrEmpty.test(editMember.getEmail())){
           if(!isEmailAvailable(editMember.getEmail())){ // Do we need this?
               throw new ResourcePersistanceException("The provided email is already registered");
           }
           foundMember.setEmail(editMember.getEmail());
        }

        return memberDao.update(foundMember);
    }

```

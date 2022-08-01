# Java

# REMINDER: Each prompt is answerable in 5min. You must record your screen as well with this prompt on the foreground.

[Here is the link for the survey to be completed after.](https://forms.office.com/r/2ty04ksdbs)

# Prompt 1

1. Name 3 linux commands and what they do.

2. What git? How does it compare to GitHub?

3. What commands must you run to save any local changes and submit those changes to github.

4. What is the main method signature and why is it important?

5. What are class in java? What three characteristics does a java class contain?

# Prompt 2

1. Name the 4 Pillars of Object Orietned Programming (OOP). Select one to explain and give an example of how it would be use.

2. Name all the methods of handling exceptions.

3. What's the difference between an error, checked exception and an unchecked exception?

4. What are annotations in Java?

5. What are generics in Java and why do we use them?

# Prompt 3

Explain the following code. Line-by-line. **_NOTE_** Answer some of the comments.

```java

public class MemberService {
    MemberDao memberDao = new MemberDao(); // why do we need this?

    public Member registerMember(Member newMember) { // What's going on in this method?
        try {

            if (!isMemberValid(newMember)) { // What's the ! doing in this conditional?
                throw new InvalidUserInputException("User input was invalid");
            }

            if(!isEmailAvailable(newMember.getEmail())){
                throw new ResourcePersistanceException("Email is already registered please try logging in.");
            }

            memberDao.create(newMember);

            return newMember;

        } catch (Exception e) { // Are the two above Exceptions being handled?
            // TODO: NEW READ ME (Lines 38-41)
            System.out.println(e.getMessage());
            return null;
        }
    }

    public boolean isMemberValid(Member newMember){ // Why do we need this method?
        if(newMember == null) return false;
        if(newMember.getEmail() == null || newMember.getEmail().trim().equals("")) return false;
        if(newMember.getFullName() == null || newMember.getFullName().trim().equals("")) return false;
        if(newMember.getExperienceMonths() < 0 ) return false;
        if(newMember.getRegistrationDate() == null || newMember.getRegistrationDate().trim().equals("")) return false;
        if(newMember.getPassword() == null || newMember.getPassword().trim().equals("")) return false;
        return true;
    }

    public boolean isEmailAvailable(String email){
        Member[] members = readAll();
        for(Member member: members){ // what is this an example of?
            if(member == null) break; // why do we need this?
            if(member.getEmail().equals(email)){
                return false;
            }
        }
        return true;
    }
}

```

[**_Here is the link for the survey to be completed after._**](https://forms.office.com/r/2ty04ksdbs)

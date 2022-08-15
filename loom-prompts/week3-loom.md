# Java Servlets & HTTP

# REMINDER: Each prompt is answerable in 5min. You'll have 25 minutes to respond to each of these questions. You must record your screen as well with this prompt on the foreground.

[Here is the link for the survey to be completed after.](https://forms.office.com/r/2ty04ksdbs)

# Prompt 1

1. What is HTTP? Why is it important?

2. Name the levels of the HTTP Status Codes and some examples of commonly seen codes.

3. What is Client-Server Architecture? What architecture do we implement in our project?

4. Name the HTTP Verbs/Methods and what they do.

5. What is JSON? Why is it so special?

# Prompt 2

1. What are Java Servlets?

2. What is a servlet container?

3. What is the lifecycle of a Servlet?

4. What methods are available on our HttpServlets? What two parameters are required?

5. Answer the following questions about the diagram:

    - Name Layers A, B & C.
    - What is Box A?
    - What is Box 1-3? What's above each of them?
    - How are any "/auth" requests handled?

    ![](https://i.imgur.com/cC64PJu.png)

# Prompt 3

Explain the following code. Line-by-line. **_NOTE_** Answer the comments.

```java

@WebServlet("/member") // What's this Annotation Used for?
public class MemberServlet extends HttpServlet implements Authable { // What's happening here?

    private final MemberService memberService;
    private final ObjectMapper objectMapper;
    private final Logger logger = LogManager.getLogger();

    // What is the purpose of making our own constructor? Does this conflict with anything?
    public MemberServlet(MemberService memberService, ObjectMapper objectMapper){
        this.memberService = memberService;
        this.objectMapper = objectMapper;
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        String email = req.getParameter("email"); // What information is this pulling?
        Member authMember = (Member) req.getSession().getAttribute("authMember"); // What's this providing? Is there every a chance this value is null?


       if(email != null) {
            logger.info("Email entered {}", email);
            try {
                Member member = memberService.findById(email);

                // What is happening in the line below?
                String payloadID = objectMapper.writeValueAsString(member);

                resp.getWriter().write(payloadID);
                resp.sendRedirect("/"); // what does this accomplish?
            } catch (InvalidUserInputException e){
                // What's happening here? What's with the {} in the String?
                logger.warn("Supplied value was not reflected in our database. Email provided was: {}", email);
                resp.getWriter().write("Email entered was not found in the database");
                resp.setStatus(404);
            }
        } else if (email != null && password != null){ // When would this run?
           Member member = memberService.login(email, password);
           String payload = objectMapper.writeValueAsString(member);
           resp.getWriter().write(payload);
       } else {
            List<Member> members = memberService.readAll();

            String payload = objectMapper.writeValueAsString(members);

            resp.getWriter().write(payload);
        }
    }


```

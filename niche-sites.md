# RFKJR Campaign Multi-Tenant Website Solution
very rough idea on how to accomplish this using a single multi-tenant application (cost efficient).  

## Approach:

### 1. Single Application with Dynamic Routing:
- Develop one application that dynamically serves content based on the URL endpoint or subdomain.
- Use a web framework like Flask or Django in Python, which are excellent for handling dynamic routing and template rendering.

### 2. Domain Routing:
- Purchase a main domain and then use subdomains (e.g., `surfers.kennedy2024.com`) or URL paths (e.g., `www.kennedy2024.com/surfers`) for each group.
- Azure Web Apps can easily handle multiple custom domains pointing to the same application.

### 3. Dynamic Content Generation:
- Create templates for each group type, and populate them dynamically based on the group’s data.
- Store static content (images, CSS specific to the group) in Azure Blob Storage and serve them efficiently using Azure CDN.

### 4. LLM Integration for Q&A Feature:
- Prepare to integrate an LLM like ChatGPT for answering user queries. Azure's managed AI services could be leveraged here for deploying and managing the model.  Doen't have to use Azure, open to any other public cloud

## Sample Flask Application Skeleton:

Here is a basic skeleton of how you could set up the Flask app to handle dynamic subdomains or paths:

```python
from flask import Flask, request, render_template

app = Flask(__name__)

# Example of dynamic route based on group
@app.route('/<group>')
def group_page(group):
    # You could further refine by checking if the group exists in your database or configuration
    return render_template(f'{group}/index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

for handling subdomains, we could use
```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def index():
    return 'Homepage for all users'

@app.route('/', subdomain='<group>')
def group_subdomain(group):
    return f'Landing page for {group}'

if __name__ == '__main__':
    app.run(debug=True)
```


## Skills Required for Volunteers

Passion for technology and a willingness to learn... everything else is a bonus; These are the skills that can be useful

### Technical Skills:

1. ** Development:**
   - Proficiency in web development,  HTML, CSS, and JavaScript.
   - Experience with Python web frameworks such as Flask or Django for backend development.

2. **Version Control:**
   - Familiarity with Git and GitHub for version control and collaborative coding.

3. **Cloud Platforms:**
   - Basic understanding of Public cloud development.  We currently have volunteer with Azure services, particularly Azure Web Apps and Azure DNS.  All public clouds welcome

4. **Database Management:**
   - Knowledge of database systems, preferably PostgreSQL or MySQL.
   - Ability to design and manage schemas, as well as integrate databases with web applications.

### Design Skills:

1. **UI/UX Design:**
   - Ability to create user-friendly web interfaces.
   - Experience with design tools like Adobe XD, Figma, or Sketch.

2. **Graphic Design:**
   - Skills in graphic design to create engaging visuals for each niche group’s landing page.
   - Proficiency in image editing tools such as Adobe Photoshop or Illustrator.

### Content Creation Skills:

1. **Copywriting:**
   - Strong writing skills to craft compelling content tailored to different groups.
   - Experience with SEO to optimize content for better visibility.

2. **Digital Marketing:**
   - Understanding of digital marketing strategies to promote the website effectively.

### Collaboration Skills:

1. **Project Management:**
   - Experience with project management tools like Trello, Asana, or Jira.
   - Ability to work efficiently in a team and manage tasks across multiple stakeholders.

2. **Communication:**
   - Excellent verbal and written communication skills.
   - Ability to coordinate with team members and stakeholders remotely.

### Optional Skills:

1. **LLM Integration:**
   - Interest or experience in integrating and managing Large Language Models (LLMs) like ChatGPT, Claude, Copilot, huggingface platform, langchain, prompt engineering techniques, etc... for interactive features.

2. **Accessibility:**
   - Knowledge of web accessibility standards to ensure the website is usable for everyone.

.

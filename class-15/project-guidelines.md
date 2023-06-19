# Ops 301 Final Project Guidelines

## Scenario & Problem Domain

You team is tasked with updating the core IT infrastructure of a recent client company acquisition. This young, innovative startup aligns well with the mission of the client company; unfortunately, its IT systems are not yet integrated into the corporate domain and cloud infrastructure.

Your team has been assigned to prototype the process of integrating these new companies. You will need to set up a VPC and Windows Server in AWS to represent existing Globex infrastructure, then practice the process of adding and organizing the new employees in Active Directory, securely connecting the acquisition's office network to the VPC, connecting local endpoints to the domain, and configuring a captive portal on a local router authenticate using Active Directory.

Remember, the purpose of this project is to **demonstrate a repeatable, efficient system** for integrating new acquisitions, not just to show off the technology itself.

Your instructor will play the role of the operations manager who has tasked you with this project, and will send you a detailed list of technical requirements.

## Assignments & Deliverables

Keep an eye on Canvas for assignments due this week. 
- Remember to complete nightly Project Report assignments. These assignments are easy to forget as you get swept up in interesting project subject matter.
- Necessities such as team agreement (conflict resolution, etc.) and project plan will be created in your Project Prep assignments. Instructor approval is required before progressing to the next Project Prep assignment.
- You will need to submit a preliminary link to your deliverables for instructor review on day 3 of project week.
- You will need to give give a practice presentation for your instructor on day 4 or project week (your instructors will schedule this). Make this as close as possible to how you plan to present on day 5 -- try not to break character, give assides or explanations, or engage in crosstalk. 
- By demo day, you'll need these deliverables assembled:
  - Demo day slide deck
  - Project report
  - Project plan
  - GitHub repo 
  - Google drive docs (if used)
- Track your individual contributions throughout the project so that you can easily submit your individual contributions writeup on demo day for grading.

## Standup

Every day, the instructional team with circulate to your group for a formal "Standup Meeting". Standup should take approximately 10 minutes per team. Some instructors will opt for a "retro" later in the day to review how things went.

> Standups give the instructional team insight into the current status of your project and the progress the team hopes to make each day.

During standup, each team member will address these three points:

  1. What you individually accomplished yesterday
  1. What you individually plan to accomplish today
  1. Anything that is blocking you from making progress

## Presentation Prep

Your team will practice your presentation prior to the final presentation day. This is typically scheduled by the instructional team. During the practice presentation, the instructional team will provide constructive feedback about the flow of the presentation and delivery of the subject matter.

Practice and prepare your technical demonstrations in advance of demo day to rule out any quirks/bugs. 

General slide deck guidelines:
- The presentation slides must use the aesthetic formatting of the [template slide deck](https://docs.google.com/presentation/d/1iv8uB6H0P49RN9IF6cYA5lpfiuL4WBGQqcbEu6Q4JAA/edit?usp=sharing).
  - Remember to create your own copy of the template and do not edit the template itself.
- Ensure your timing is no more than 20 minutes long, including some time at the end for questions. 
- Present from the final product, deployed site, or official documentation that you produce.
- Each member should introduce themselves with their personal pitch.   
  - The "About Us" page provides a great backdrop for this portion of the presentation.

Each member of the team must have a speaking part. It is okay to use presenter notes/outlines but remember to avoid reading notes verbatim and to present naturally as if speaking to a friend.

The appropriate dress code is business casual - not too formal and not too casual. 

Be cognizant of the environment you're presenting from. A clean backdrop, good lighting, and quality mic and webcam go a long ways.

In addition to the scheduled practice session, the team is encouraged to continue to practice on their own. Keep track of the time and adjust accordingly. Practice transitioning speaking segments.

Speak clearly and do not use slang or profanity. Take it seriously and be professional.

## Grading

Each team member's grade is split between their individual effort, and the project's technical merit.

Individual effort is graded based on contributions to project deliverables, and professionalism in the presentation.

Technical merit of the project overall is evaluated according the requirements. The Project Grade is a combination of the Presentation (50%) and the Deliverables (50%)

### Presentation (50%)

Components of the presentation must include:

#### Team members individually introduce themselves. (5 min)
- One interesting/fun fact about yourself
- Your career ambitions (where you've been, where you're going, and why)
#### Topical Overview (5 min)
- As the "Problem Domain", describe the project scenario you were assigned and the overall client requirements.
- What solutions to the problem domain will your team be presenting today? Why did you choose these solutions?
- Explain and define any key terms you use, such as DNS, DHCP, Static IP. Your audience is both technical and non-technical, and they need to be able to follow along with your presentation.
#### Improvements made to network infrastructure to accommodate remote employees and site-to-site connectivity (5 min)
- Implementation of virtual private networking (VPN) and demonstrate successful resource access
- Network access controls system
  - How does your system achieve AAA network security management principles?
#### Final thoughts on how the project went (5 min)
- The team's approach to planning and communication throughout the project
- A technical obstacle or two and how those obstacles were overcome
- A portion of the outcome that each team member is particularly proud of
#### Q&A (5 min)
- All team members should contribute to answering questions

### Deliverables (50%)

Submit to instructor a single link to your Github Org. All team members are to contribute an equal share to documentation corresponding to the components they worked on and should clearly indicate which components each contributed to in their individual project submission notes.

#### **GitHub Repository (10%)**
* An appropriately name Github "Organization"
  * Sufficient documentation in the top level README to explain to a stranger who you are, what this project was about, and how all of the material in the repo pertains to it.
    * This README should be:
      * Attractively formatted
      * Include links to relevant files and repos.
      * Include links to each of your own Github accounts AND LinkedIn accounts.
* Separate repositories for:
  * Presentation and Project Organization materials.
  * SOPs, Topologies, and other documentation.
  * Scripts.
* Each of these repositories should have attractive and informative `README.md`, and well labeled links to any relevant files within the repo.
* Systems Documentation:
  - Include in your deliverable any relevant information required for the operation of the demonstrated systems.
  - Any config files which you created or customized, exported in an appropriate format (such as json)
#### **Presentation Material (5%)**
- Slide deck, as a PDF
- A link to the video of your presentation (when it becomes available)
#### **Scripts and Automation (5%)**
- Include any Scripts written in the course of the project.
#### **Network design (20%)**
- A clear, written explaination and justification your network design.
  - Include a table or chart of network infrustructure and configuration details (yes, this will overlap with your topology -- you must document your network in both ways):
    - Subnets and their uses
      - Include Subnet Masks, CIDR addresses, etc.
    - DHCP ranges
      - Lease pools
      - Ranges of addresses reserved for particular uses
    - Firewall rules
    - Roles and IP address of all important devices (everything but endpoints)
- A network topology diagram of your systems architecture design.
  - All components must be labeled, and network diagram must be presentable (straight lines) and free of defects/typographical issues. Take your time to create a quality network diagram; do not rush!
  - Clearly indicate what devices are hosting network services, like DHCP, DNS, etc.
  - Include enough information (such as computer names, OS types, IPs etc.) to be useful, but this will be paired with written explanation and infrastructure chart, which should be more exhaustive.
#### **SOP and Policy Documentation (10%)**
- SOP Requirements:
  - Each SOP should include the following sections:
    - Purpose
    - Scope
    - Responsibilities
    - Prerequisites
    - Procedures
    - References
    - Definitions
    - Revision History (including who contributed to each revision)
  - For **each** SOP included in your MSP SOW deliverable, attribute authorship to the team member
  - SOPs can either be:
    - Worked on as google docs and submitted as PDFs
    - Worked on and submitted as Markdown files
  - SOPs should share a common format (see [SOP-example-template](./SOP-example-template.md))
  - SOPs should be submitted either as individual documents or as a single document (either PDF or Markdown) with a linked table of contents
- Compose thorough SOPs for each of the following:
  - How will network account needs be handled for employees being onboarded?
  - How will network account needs be handled for employees being terminated?
  - How will OS version control be handled?
    - Hint: Read [Windows Server Update Services](https://docs.microsoft.com/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus){:target="_blank"}.
  - How will you ensure users can access their files from any domain attached system?
  - How will you monitor network traffic?
  - How will you manage change to the network (such as hardware, software, or configuration changes) while minimizing network disruptions and downtime?
  - How will you manage and maintain network security?

Teams are encouraged to ask their instructional team for feedback on project report, slide deck, and other deliverables. The client point of contact should be contacted via email regarding scenario-specific scoping.

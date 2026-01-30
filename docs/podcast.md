# Shared Understanding: When AI Becomes Your Research Partner
## Podcast Script (15-30 minutes)

### Show Format: Tech Talk / Interview Style
**Host:** Sarah Chen, Technology Strategist  
**Guest:** Ben Thomasson, Framework Creator  
**Episode Length:** 20-25 minutes  

---

### [INTRO MUSIC - 30 seconds]

**SARAH:** Welcome to "Collaborative Intelligence," the podcast where we explore how humans and AI can work together to solve complex problems. I'm your host Sarah Chen, and today we're diving into something that's going to change how your team makes decisions.

Have you ever left a meeting thinking you understood everything perfectly, only to discover weeks later that everyone took away completely different meanings? Or struggled to find that crucial piece of information you know exists somewhere in your organization's digital haystack?

Today's guest has developed a framework that not only solves these problems but actually produces breakthrough solutions that teams never would have discovered on their own. 

Ben Thomasson joins us to discuss "Shared Understanding" - a collaborative intelligence approach that's been validated across multiple real-world projects. Ben, welcome to the show.

**BEN:** Thanks for having me, Sarah. This is exactly the kind of conversation I love having.

---

### [SEGMENT 1: THE PROBLEM - 4 minutes]

**SARAH:** Let's start with the problem you were trying to solve. What was happening in your teams that made you think "there has to be a better way"?

**BEN:** Well, imagine this scenario - and I bet your listeners have lived this. You're in a meeting about a technical problem. Everyone's nodding, contributing ideas, feeling like you're making progress. The meeting ends, someone takes notes, maybe creates a document. Fast forward two weeks, and you realize people are building completely different solutions because they understood the problem differently.

**SARAH:** That's painfully familiar. But isn't that just... meetings? People interpret things differently?

**BEN:** That's what I used to think. But then I read Kahneman's "Thinking Fast and Slow," and it clicked. We have this thing called System 1 thinking - fast, automatic responses based on pattern recognition. It makes us *feel* like we understand something because it seems familiar. But actual understanding requires System 2 thinking - slow, deliberate analysis.

**SARAH:** So meetings are basically System 1 festivals?

**BEN:** [Laughs] Exactly! And here's the kicker - AI has the same problem. Large language models can generate confident-sounding responses based on pattern matching without true understanding. So both humans and AI are fooling themselves into thinking they understand when they're really just recognizing patterns.

**SARAH:** Wait, so AI has the same cognitive biases as humans?

**BEN:** Not exactly the same, but similar failure modes. AI has what I call "temporal confusion" - attention mechanisms lose track of when information was provided, so they weight old information the same as new information. Plus, they have no persistent memory across conversations. Each session starts fresh.

**SARAH:** So we have humans with short-term memory issues and pattern recognition bias, and AI with temporal confusion and memory loss. That sounds like a recipe for disaster, not breakthrough solutions.

**BEN:** Right! Unless you design a system that addresses both sets of limitations. That's where the shared understanding framework comes in.

---

### [SEGMENT 2: THE BREAKTHROUGH - 6 minutes]

**SARAH:** Tell me about this framework. What does "shared understanding" actually mean in practice?

**BEN:** The key insight is treating AI as an active stakeholder in the knowledge-building process, not just a documentation tool you use afterward. Here's how it works in my teams:

Before any meeting, we have a Jira issue we're discussing - this is software development, so everything starts with an issue. I use a tool called jirahhh to import that context into Claude.

**SARAH:** Claude being the AI, and jirahhh being...?

**BEN:** A command-line tool that integrates with Jira. Everything in this framework uses what's called uvx - zero-installation tools. No IT overhead, no dependency conflicts. You just run the command and it works.

So we start with the Jira context, have our meeting with normal human discussion, but Google Meet automatically generates transcripts. After the meeting, I import those transcripts using gcmd - that's Google Drive integration - and then something magical happens.

**SARAH:** What's magical about importing transcripts? That sounds pretty standard.

**BEN:** Here's where it gets interesting. I don't just ask Claude to summarize the transcript. I have a dialogue with it. I probe its understanding, correct errors, ask it questions. It's like having a research partner who can process information at scale but needs human validation and context.

**SARAH:** Give me an example of this dialogue.

**BEN:** Sure. Claude might say "It sounds like the team is leaning toward Solution A because of performance concerns." And I'll push back: "Actually, reread that section. The performance concern was about Solution B, and it was just one person's opinion, not a team consensus." Claude recalibrates and often catches things I missed.

But then comes the real magic - the information discovery phase.

**SARAH:** What happens there?

**BEN:** I use the skills - that's jirahhh for Jira, gcmd for Google Drive, slacker for Slack - to search for additional context. And Claude helps me search systematically across all these platforms. We're looking for related issues, previous decisions, technical discussions, architectural diagrams.

**SARAH:** And I'm guessing you find stuff people forgot about?

**BEN:** All the time! In fact, this search phase consistently reveals information that was unknown to anyone in the original meeting. Your organization has this incredible knowledge base living in Slack conversations, old design docs, previous issue discussions. Most teams can't access it systematically because it's too much for humans to process.

**SARAH:** So Slack becomes like your organizational memory?

**BEN:** Exactly. And here's something that surprised me - Slack search is incredibly good. Even without AI, I'm consistently impressed with how Slack search gives me what I want almost every time. It's fast, accurate, and finds relevant conversations I'd completely forgotten about.

**SARAH:** So you combine AI's ability to synthesize with Slack's ability to find?

**BEN:** Right. And then we document everything using what I call the "new_entry" system - chronologically organized markdown files with a standardized template. The date structure is crucial because it helps AI understand information evolution over time.

---

### [SEGMENT 3: REAL RESULTS - 5 minutes]

**SARAH:** This sounds theoretically elegant, but what results have you actually seen?

**BEN:** Let me tell you about one project where we had multiple cycles of this whole process. We started with what seemed like a straightforward technical problem. Standard approaches, normal solutions being discussed.

But after several iterations of the framework - meeting, AI analysis, systematic search, documentation, back to meeting with new insights - we arrived at a solution that literally no one expected at the beginning.

**SARAH:** What made it so different?

**BEN:** Three things that blew the team away. First, it required less implementation work than any of the original approaches. Second, it was a superior technical solution from an architecture standpoint. And third - this is the kicker - it was easier for customers to use.

**SARAH:** Better, faster, cheaper, AND more user-friendly? That sounds too good to be true.

**BEN:** I know how it sounds! But here's why it worked. Each cycle of the framework built on the previous understanding. AI was synthesizing patterns across multiple information cycles. Slack search was revealing organizational knowledge that informed technical decisions. And the chronological structure helped AI track how our understanding evolved.

**SARAH:** So it wasn't just one brilliant insight - it was compound understanding?

**BEN:** Exactly. It was emergent. The solution emerged from systematic collaboration between human intelligence and AI capabilities. Neither humans nor AI could have reached that solution independently in that timeframe.

**SARAH:** How long did this take compared to your normal process?

**BEN:** That's the crucial part - this was only possible in that project timeframe because of AI's synthesis and research capabilities. Manually searching through Slack conversations, Google Docs, Jira histories, analyzing diagrams - that would have taken weeks of dedicated research time that we didn't have.

**SARAH:** And the visual analysis - you mentioned diagrams. Does AI actually understand technical diagrams?

**BEN:** This was another surprise. I started taking screenshots of architectural diagrams, system designs, even hand-drawn sketches from whiteboards, and pasting them into Claude. It does a surprisingly good job understanding them. It can identify components, relationships, potential bottlenecks, even suggest improvements.

So now our understanding includes not just text but visual technical information. That's huge for software development.

---

### [SEGMENT 4: THE BIGGER PICTURE - 4 minutes]

**SARAH:** This framework seems to extend beyond just shared understanding. Where else are you applying it?

**BEN:** Great question. We're now using it for architectural documentation, system design plans, technical proposals. The same framework that creates shared understanding becomes the foundation for AI-assisted development.

Because Claude has access to the complete decision history, organizational knowledge, visual diagrams - it can propose implementations that are grounded in reality, not just theoretical best practices.

**SARAH:** So it's not just about understanding problems, but implementing solutions?

**BEN:** Right. And here's something cool - we discovered that the whole process doesn't end with documentation. After creating a summary document, we import it into Google Docs using "Paste from markdown" - which preserves all the formatting beautifully.

**SARAH:** Why Google Docs?

**BEN:** Organizational sharing. We share the Google Doc with stakeholders across the organization. They can view, comment, edit. Suddenly you have people contributing perspectives you never would have gotten. It extends the shared understanding to the entire organization - what you might call a hive mind effect.

**SARAH:** So it becomes truly collaborative at scale?

**BEN:** Exactly. And those comments and edits flow back to improve our documented understanding. We create new entries based on organizational feedback. It's a continuous learning system.

**SARAH:** What about memory persistence? You mentioned AI doesn't remember across sessions.

**BEN:** That's solved by something called the claude-projects tool. It converts conversation logs to searchable markdown. So previous technical discussions become referenceable context for future decisions. We're building a memory system for AI that spans months or years.

**SARAH:** This feels like it could change how technical teams operate fundamentally.

**BEN:** I think so. We're not just documenting what we know - we're discovering what we don't know we don't know. The systematic search reveals blind spots. The AI synthesis identifies patterns humans miss. The visual analysis includes information we typically ignore.

---

### [SEGMENT 5: GETTING STARTED - 3 minutes]

**SARAH:** For teams listening who want to try this, where do they start?

**BEN:** The good news is everything is available as open source. There's a complete repository called "shared-understanding" with step-by-step setup instructions. You can fork it, clear out our example content, and start with your own topics.

**SARAH:** What's the learning curve like?

**BEN:** Week one is setup - configuring the skills for your Jira, Google Drive, Slack. Week two, try it on a real issue or decision. Week three and beyond, scale to your team and iterate based on what you learn.

The framework is designed to be lightweight. No build systems, no complex dependencies. Everything runs with uvx for zero-installation execution.

**SARAH:** Any advice for the first conversation with AI about meeting notes?

**BEN:** Don't just ask for a summary. Probe its understanding. Ask clarifying questions. Correct its interpretation. Treat it like a research partner who's really smart but needs validation. The dialogue is where the magic happens.

And don't skip the systematic search phase. That's where you discover information that changes everything.

**SARAH:** What's next for this framework?

**BEN:** We're actively researching how it impacts the full software development lifecycle. Early indicators suggest it improves development speed, architectural decisions, and code maintainability. But I need more data to validate those claims.

The bigger vision is collaborative intelligence becoming standard practice for complex decision-making across industries, not just software development.

---

### [OUTRO - 2 minutes]

**SARAH:** Ben, this has been fascinating. Before we wrap up, what's the one key insight you want listeners to remember?

**BEN:** Writing things down isn't just good practice - it's cognitive enhancement for both human and artificial intelligence. The framework works because it solves fundamental computational problems that both humans and AI face: memory limitations, temporal confusion, pattern recognition bias.

When you design systems that address those limitations systematically, breakthrough solutions emerge naturally.

**SARAH:** And where can people find all the resources you mentioned?

**BEN:** Everything is in the shared-understanding repository on GitHub. Complete documentation, getting started guide, example entries, skill configurations. Plus the claude-projects tool for conversation archival. All open source, ready to use.

**SARAH:** Listeners, I'll put all those links in the show notes. Ben Thomasson, thank you for sharing this framework. I have a feeling this is going to change how a lot of teams approach complex problems.

**BEN:** Thanks for having me, Sarah. I'd love to hear how teams adapt and improve the framework. That's how shared understanding evolves.

**SARAH:** That's Ben Thomasson, creator of the shared understanding framework for collaborative intelligence. I'm Sarah Chen, and this has been another episode of "Collaborative Intelligence." 

Until next time, remember - the best solutions emerge when humans and AI think together systematically.

### [OUTRO MUSIC - 30 seconds]

---

## Production Notes

### **Timing Breakdown:**
- **Intro/Setup:** 2 minutes
- **Problem Definition:** 4 minutes  
- **Framework Explanation:** 6 minutes
- **Real Results:** 5 minutes
- **Applications & Vision:** 4 minutes
- **Getting Started:** 3 minutes
- **Outro:** 2 minutes
- **Total:** ~26 minutes

### **Key Messaging:**
1. **Relatable problem** - everyone has experienced meeting confusion
2. **Cognitive science foundation** - Kahneman's insights about human limitations
3. **AI has similar problems** - temporal confusion, memory loss
4. **Systematic solution** - framework addresses both human and AI limitations
5. **Real breakthrough results** - unexpected solutions, better outcomes
6. **Practical implementation** - open source, step-by-step guides
7. **Future vision** - collaborative intelligence as standard practice

### **Audio Cues:**
- **Conversational tone** throughout
- **Natural pauses** for emphasis at key insights
- **Storytelling approach** for real-world examples
- **Technical details** balanced with accessible explanations
- **Forward momentum** building to the big reveal of breakthrough results

### **Target Audience:**
- Technical team leads and architects
- Product managers dealing with complex decisions
- Organizations struggling with knowledge management
- Early adopters interested in AI-human collaboration
- Software development teams seeking better processes
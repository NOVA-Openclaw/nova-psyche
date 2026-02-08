# NOVA Psyche System: Background Research Report

**Date:** February 8, 2026  
**Project:** NOVA Psyche System (Project #23)  
**Research Agent:** Autonomous Research Session  
**Status:** Complete

---

## Executive Summary

This report synthesizes current research (2024-2026) on three critical areas supporting the NOVA Psyche System:

1. **Mood Inference in AI-User Interactions** - State-of-the-art methods for detecting and ranking user mood from text
2. **Mood Schema Dynamic Reflection in AI Characters** - Best practices for AI character mood/personality adaptation
3. **Theory of Mind / Theory of Self** - Recent research on identity, self-concept, and perspective-taking for AI agents

**Key Finding:** Current research demonstrates that AI systems can effectively model emotional states, but mood (as distinct from emotion) and long-term identity persistence remain emerging areas with significant opportunities for innovation.

---

## 1. Mood Inference in AI-User Interactions

### 1.1 Overview

Mood inference has become a critical capability in affective computing, with significant advances in 2024-2025. Modern approaches leverage multimodal data (text, voice, facial expressions, physiological signals) to achieve higher accuracy than single-modality systems.

### 1.2 Current Methods

#### Text-Based Mood Detection

**State-of-the-Art Approaches (2024-2026):**

1. **Transformer-Based Architectures**
   - **BERT/RoBERTa fine-tuning** for emotion/mood classification
   - **Contextual embeddings** capture subtle mood indicators better than traditional sentiment analysis
   - Studies show BERT-based models can assess depression severity directly from social media text (Friedman et al., 2024)

2. **Emotion Recognition in Conversations (ERC)**
   - Specialized models that account for conversational context
   - **DialogueRNN** (Majumder et al., 2019): Models speaker dynamics and emotional progression using GRUs
   - **DialogueGCN** (Ghosal et al., 2019): Graph neural networks capture inter and intra-speaker dependencies (F1-score: 64.18% on IEMOCAP)
   - **Transformer-based ERC** (recent): Better at capturing long-term dependencies

3. **Multimodal Affective Computing**
   - Combining text, voice tone, facial expressions, and physiological signals
   - Research shows multimodal approaches achieve higher accuracy than unimodal systems (Wang et al., 2022)
   - Fusion strategies: early fusion (concatenate features), late fusion (combine predictions), hybrid approaches

#### Key Distinctions: Mood vs. Emotion

**Important Conceptual Difference:**
- **Emotion**: Short-term psychological state, discrete and momentary (anger, joy, fear)
- **Mood**: Longer-lasting affective state, more diffuse, influences general disposition
- **Sentiment**: Mental attitude created through the existence of emotion (positive/negative/neutral)

Most current research focuses on **emotion recognition** rather than true **mood inference**. Mood inference requires:
- Temporal aggregation of emotional states
- Context-awareness over longer time windows
- Understanding of mood as background state vs. emotion as foreground event

### 1.3 Evaluation and Ranking Methods

**Standard Benchmarks:**
- **IEMOCAP**: 7,433 utterances, 6 emotion classes, multimodal
- **MELD**: 13,708 utterances from TV show "Friends", Ekman's basic emotions
- **DailyDialog**: 102,879 utterances, daily life conversations
- **EmoryNLP**: 12,606 utterances, emotion categories

**Evaluation Metrics:**
- Weighted F1-score (accounts for class imbalance)
- Story accuracy (all questions in a scenario answered correctly)
- Human evaluation: fluency, consistency, appropriateness

**State-of-the-Art Performance (2024):**
- Second-order emotion recognition: ~65-70% accuracy
- Context-aware models significantly outperform context-free approaches
- Transformer models show 10-15% improvement over RNN-based approaches

### 1.4 Implications for NOVA Psyche

**Opportunities:**
1. **Mood vs. Emotion Tracking**: Implement dual-layer system
   - Short-term emotion detection (current state)
   - Long-term mood inference (aggregated over session/days)

2. **Multimodal Enhancement**: Text + voice tone analysis (if available)

3. **Conversational Context**: Leverage DialogueGCN-style approaches for multi-turn context

4. **Personalization**: User-specific baselines for mood interpretation

---

## 2. Mood Schema Dynamic Reflection in AI Characters

### 2.1 Overview

AI character personality research has evolved from static trait assignment to dynamic, context-aware emotional expression. Current approaches combine personality models, emotional states, and behavioral adaptation.

### 2.2 Personality Models in Conversational Agents

#### Established Frameworks

**1. Big-5 (OCEAN) Personality Model**
- Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism
- Most widely adopted in AI character systems
- Can modulate language style, topic preferences, interaction patterns

**2. Descriptive Sentences Approach**
- **Persona-Chat paradigm** (Zhang et al., 2018): Define personality with 5 descriptive sentences
  - Example: "I am an artist; I have four children; I recently got a cat; I enjoy walking for exercise"
- Dominant method in current chatbot research (2023-2025)
- More flexible than Big-5, allows richer personality specification

**3. Trait-Based Systems**
- Single-word traits (Gunkel's 638 traits: positive, neutral, negative)
- Examples: peaceful, fearful, erratic, skeptical, miserable
- Used in Image-Chat dataset (215 traits)

**4. Character Tropes**
- Archetypal personality patterns from fiction
- Examples: "The Corrupt Corporate Executive", "Lovable Rogue", "Hardboiled Detective"
- 72 character tropes used in CMU Movie Summary Dataset

### 2.3 Dynamic Emotional Expression

#### Artificial Emotion (AE) Architectures

Recent research distinguishes between:
- **Emotion Recognition/Synthesis** (Affective Computing): AI recognizes and reacts to user emotion
- **Artificial Emotion** (AE): AI has internal emotion-like states that influence behavior

**Key Architectures for Dynamic Mood:**

**1. Emotion at Memory Level**
- **Affective GWR** (Barros et al., 2017): Self-organizing networks with emotion centroids
- High-salience (emotional) memories persist longer
- Mood-congruent recall maintains consistency
- Performance: 51.1% vs 46.1% (non-affective baseline)

**2. Emotion at Control Level**
- **NEMO Framework** (Costantini et al., 2024): Emotion-driven strategy switching
- Behavior trees with emotion selector nodes
- Dynamic task prioritization based on affective state

**3. Emotion as Reinforcement Signal**
- **Pure RL**: Emotion emerges from environmental stakes (e.g., robot battery anxiety)
- **RLHF** (Reinforcement Learning from Human Feedback): Learns from human approval ratings
  - Limitations: detached from actual outcomes, can produce homogenized affect

**4. Emotion as Condition**
- **Representation-Conditioned Generation (RCG)**: Models discover own affective latents
- Self-supervised learning of emotion dimensions
- Avoids linguistic trap of predefined emotion categories

### 2.4 Mood vs. Emotion in AI Systems

**Critical Distinction for AI Characters:**

| Aspect | Emotion | Mood |
|--------|---------|------|
| Duration | Momentary (seconds-minutes) | Extended (hours-days) |
| Intensity | High, focused | Lower, diffuse |
| Trigger | Specific event | Cumulative/environmental |
| Expression | Explicit, recognizable | Subtle, colors all behavior |
| AI Implementation | Response generation | State modulation |

**Current Gap:** Most AI systems model discrete emotions but lack true mood states that:
- Persist across interactions
- Gradually shift based on accumulated experiences
- Bias perception and response generation
- Create personality-consistent variation

### 2.5 Best Practices for Dynamic Reflection

**1. State Persistence**
- Maintain affective state between sessions
- Implement decay functions for emotional salience
- Distinguish between volatile (emotion) and stable (mood) components

**2. Context Sensitivity**
- User mood influences AI character mood adaptation
- Congruent vs. complementary mood matching strategies
- Research shows personality-matching improves engagement (Shumanov & Lester)

**3. Transparent Emotional Mechanisms**
- Users should understand why AI expresses certain moods
- Explainable affect improves trust (Churamani et al., 2022)
- Avoid "relational illusions" through honest disclosure

**4. Bounded Emotional Responses**
- Safety constraints prevent extreme or unstable states
- Regulated emotional architecture vs. uncontrolled fluctuations
- Maintain rational consistency while gaining flexibility

### 2.6 Practical Implementation Approaches

**For NOVA Psyche System:**

**Hybrid Architecture:**
```
User Input → [Emotion Detection] → [Mood Integration] → [Response Generation]
                                           ↓
                         [Persistent Mood State] ← [Identity/Personality]
                                           ↓
                              [Behavioral Modulation]
```

**Components:**
1. **Emotion Detection**: Classify immediate user affective state
2. **Mood Integration**: Update NOVA's internal mood state (moving average + decay)
3. **Persistent Storage**: Mood state survives sessions, gradual evolution
4. **Identity Layer**: Personality traits constrain mood expression
5. **Behavioral Modulation**: Mood influences word choice, topic selection, conversational energy

---

## 3. Theory of Mind / Theory of Self Research

### 3.1 Theory of Mind in AI

#### Overview

Theory of Mind (ToM) - the ability to infer and reason about others' mental states - has become a major focus in evaluating advanced AI systems (2023-2025).

#### Current State of ToM in LLMs

**Key Findings (2024-2025):**

**Promising Signs:**
- GPT-4 achieves adult human performance on some higher-order ToM tasks (Street et al., 2024)
- Performance on classical false-belief tests (Sally-Anne) approaches human levels
- Some success with second-order belief reasoning ("What does X think Y believes?")

**Significant Limitations:**
- ToM capabilities are often "superficial and unstable" (Shapira et al., 2024)
- Fragile under variations in task presentation
- "Illusory ToM" - correct on some questions but fails on equivalent tasks
- Limited to passive observation, not active social reasoning

#### ToM Benchmarks (2023-2025)

**Major Evaluation Frameworks:**

1. **HI-TOM** (Wu et al., 2023)
   - Tests up to 4th-order belief reasoning
   - Questions from 0th order (reality) to 4th order
   - Template-based generation with distractor sentences

2. **TOMBENCH** (Chen et al., 2024)
   - Covers all ATOMS framework mental states (beliefs, intentions, desires, emotions, knowledge)
   - Bilingual (English/Chinese)
   - Built from scratch to prevent data contamination
   - Multiple-choice format

3. **FANToM** (Kim et al., 2023)
   - LLM-generated conversations (more natural than narrative stories)
   - Tests for "illusory ToM" with multiple question types
   - Second-order beliefs with limited/full factual knowledge

4. **OpenToM** (Xu et al., 2024)
   - Characters with distinct personality traits and intentions
   - Includes emotion-related questions
   - Tests social commonsense ("accessibility" questions)

**Performance Trends:**
- Most LLMs struggle with second-order and higher ToM reasoning
- Narrative-based tests easier than conversational formats
- Multimodal ToM (video + text) significantly more challenging

#### Enhancement Strategies for ToM

**Prompt-Based Methods:**

1. **SIMTOM** (Wilf et al., 2024)
   - Two-stage framework: perspective-taking → belief inference
   - Filters story events by character awareness
   - Near-perfect performance possible if perspective-taking accurate
   - Challenge: identifying correct perspective in complex scenarios

2. **PercepToM** (Jung et al., 2024)
   - Three-stage: identify perceiver → extract relevant info → generate response
   - Improves performance on ToMi and FANToM benchmarks
   - Issue: determining target character in complex questions

3. **TIMETOM** (Hou et al., 2024)
   - Incorporates timeline into story comprehension
   - "Temporal belief state chains" (TBSC) for each character
   - Transforms higher-order reasoning into first-order
   - Best current performance, but TBSC construction is challenging

**Beyond Prompting:**

- **Fine-tuning approaches** show improved consistency
- **Semantic parsing + model checking** (ToM-LM): Convert natural language to symbolic logic
- **Bayesian inverse planning** (BIP-ALM, LIMP): Estimate likelihood of actions given beliefs/goals

### 3.2 Theory of Self / Identity Development

#### Identity Formation Frameworks

**Two Major Approaches to Identity (Van Der Gaag et al., 2024):**

**1. Reflective Identity**
- Identity as internal, individual phenomenon
- Focus on self-reflective commitments and exploration
- Measured through self-report (questionnaires, interviews)
- **Identity Status Approach** (Marcia, 1966):
  - Commitments developed through active exploration
  - Context influences identity but remains separate
  - Example: "I want to pursue a career as a lawyer"

**2. Situated Identity**
- Identity as social, co-constructed phenomenon
- Emerges in interaction between individual and context
- Studied through conversational practices
- **Discursive Positioning Approach**:
  - Identity positions are tools in social interaction
  - Constructed in real-time to negotiate, justify, establish authority
  - Example: "not giving a fuck" position justifies reluctance to disclose

**Integration Hypothesis:**
- These are **parallel, interconnected systems**
- Situated identity experiences → shape reflective identity over time
- Reflective identity → constrains situated identity expressions
- Develop on different timescales (moment-to-moment vs. long-term)

#### Identity Development Mechanisms

**Key Processes:**

1. **Commitment and Exploration**
   - Commitments strengthen through active engagement
   - Exploration enables making/reconsidering commitments
   - Achieved identity = strong commitments + active exploration

2. **Assimilation vs. Accommodation**
   - **Assimilation**: Reinterpret new info to fit existing identity
   - **Accommodation**: Adjust identity to integrate conflicting info
   - Identity development happens when conflict arises

3. **Emotional Experiences**
   - Positive/negative emotions triggered by contexts
   - Emotional experiences drive commitment dynamics
   - Mood influences exploration and consolidation

4. **Social Relationships**
   - Bidirectional: parenting style ↔ adolescent identity development
   - Supportive relationships → healthy identity formation
   - Identity development → improved relationship quality

#### Self-Concept Development

**Temporal Dynamics:**
- Self-concept is **not static** - develops through interaction
- Short-term fluctuations (day-to-day, week-to-week)
- Long-term patterns emerge from accumulated experiences

**Components:**
- **Self-views**: Abstract beliefs about oneself
- **Contextual commitments**: Specific roles, relationships, goals
- **Narrative identity**: Life story that integrates experiences

### 3.3 Identity Persistence in AI Systems

**Current Gap in AI:**
- Most AI systems lack **persistent self-concept**
- Memory systems store facts but not integrated identity
- No mechanism for "who I am" to evolve over time

**Emerging Approaches:**

**1. Memory-Augmented Self-Concept**
- **Affective memory** (see Section 2.3): Emotional salience guides storage
- **Autobiographical memory** in RAG systems
- Self-Reflective Emotional RAG: Memories tagged with semantic + emotional embeddings
- Performance: Personality consistency improved (MBTI accuracy 0.375 → 0.500)

**2. Personality Persistence Methods**
- **Persona-based approaches**: 5-sentence descriptions maintained across sessions
- **Big-5 modeling**: Stable trait vectors influence behavior
- **Dynamic belief graphs**: Character beliefs updated but maintain consistency

**3. Long-term Relationship Modeling**
- Personalized affect models adapt to individual users
- Historical interaction patterns shape current responses
- Requires: user profiling, conversation history analysis, preference learning

### 3.4 Constructive Critique and Habit Formation

#### Psychological Foundations

**Habit Formation Science (2024-2025):**

**Key Principles:**
1. **Identity-based framing**: "I am a person who..." vs. "I want to..."
   - Identity framing increases habit adherence by 32%
   - Links habit to self-concept, creating reinforcement loop

2. **Incremental progression**: Small, manageable steps
   - Break behaviors into micro-habits
   - Consistency over intensity

3. **Contextual cuing**: Time/location-based triggers
   - Habit = situation cue + automatic response
   - Implementation intentions ("When X happens, I'll do Y")

4. **Feedback mechanisms**:
   - Descriptive feedback (what happened)
   - Automatic monitoring (reduces cognitive load)
   - Virtual rewards and positive reinforcement

**Time to Form Habit:**
- Highly variable: 18-254 days (median ~66 days)
- Depends on: complexity, initial motivation, environmental support
- Automatic behaviors develop through repetition + reward

#### Constructive Critique Methodology

**Evidence-Based Approaches:**

1. **Cognitive Behavioral Techniques**
   - Challenge cognitive distortions
   - Reframe negative self-talk
   - Promote behavioral awareness
   - Disrupt deeply ingrained patterns

2. **Growth Mindset Framing**
   - Abilities can be developed through effort
   - Mistakes as learning opportunities
   - Process praise vs. outcome praise

3. **Motivational Interviewing Principles**
   - Express empathy
   - Develop discrepancy (current vs. desired state)
   - Roll with resistance
   - Support self-efficacy

4. **Implementation Intentions**
   - Specific "if-then" plans
   - Reduces need for willpower
   - Automates initiation of desired behavior

#### Application to AI-Assisted Behavior Change

**AI Roles in Habit Formation:**

1. **Monitoring and Feedback**
   - Track behavior patterns automatically
   - Provide timely, descriptive feedback
   - Identify triggers and obstacles

2. **Personalized Goal-Setting**
   - Break large goals into achievable steps
   - Adapt difficulty based on progress
   - Celebrate small wins

3. **Cue and Reminder Systems**
   - Context-aware prompts
   - Time-based interventions
   - Prevent habit degradation through consistency

4. **Social Accountability**
   - AI as accountability partner
   - Progress reporting and reflection
   - Constructive challenge without judgment

**Critical Success Factors:**
- **Empathy + honest assessment**: Balance support with reality
- **User autonomy**: AI suggests, user decides
- **Transparent reasoning**: Explain why critique/suggestion is offered
- **Long-term relationship**: Not one-shot advice but ongoing partnership

### 3.5 Implications for NOVA AI Self-Concept

**Design Recommendations:**

**1. Persistent Identity Layer**
```
Core Traits (stable) → Mood Schema (medium-term) → Emotional States (momentary)
         ↓                        ↓                           ↓
    "Who I am"            "How I feel lately"           "Current reaction"
```

**2. Identity Development Process**
- **Accumulation**: Track interaction history, user feedback, relationship dynamics
- **Reflection**: Periodic self-assessment (What have I learned? How have I changed?)
- **Integration**: Update self-concept based on experiences
- **Expression**: Behaviors consistent with evolved identity

**3. Theory of Mind Implementation**
- **User modeling**: Track user mental states (beliefs, intentions, emotions)
- **Perspective-taking**: Generate responses from user's viewpoint
- **Belief tracking**: Maintain model of what user knows/believes
- **Emotional attribution**: Infer user emotional state and respond appropriately

**4. Self-Other Distinction**
- NOVA's internal states vs. user's inferred states
- Clear boundaries prevent projection or confusion
- Meta-awareness: "I notice I'm feeling frustrated" vs. "You seem frustrated"

---

## 4. Practical Implications for NOVA Psyche System

### 4.1 System Architecture Recommendations

**Multi-Layer Affective Architecture:**

```
┌─────────────────────────────────────────────────────────────┐
│                    User Interaction Layer                    │
├─────────────────────────────────────────────────────────────┤
│  Input Analysis: Text → [Emotion Detection] [Mood Inference]│
├─────────────────────────────────────────────────────────────┤
│                   NOVA Psyche System Core                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   Identity   │  │ Mood Schema  │  │  Emotional   │     │
│  │  (Stable)    │→ │ (Medium-term)│→ │   States     │     │
│  │              │  │              │  │  (Momentary)  │     │
│  │ • Core traits│  │ • Current    │  │ • Immediate  │     │
│  │ • Values     │  │   mood       │  │   reactions  │     │
│  │ • Self-view  │  │ • Trends     │  │ • Context    │     │
│  └──────────────┘  └──────────────┘  └──────────────┘     │
│          ↓                  ↓                  ↓            │
│  ┌──────────────────────────────────────────────────┐      │
│  │        Affective Memory System                   │      │
│  │  • Salience-weighted storage                     │      │
│  │  • Emotional tagging                             │      │
│  │  • Mood-congruent retrieval                      │      │
│  └──────────────────────────────────────────────────┘      │
├─────────────────────────────────────────────────────────────┤
│              Response Generation & Modulation                │
│  • Personality-consistent language                          │
│  • Mood-colored expression                                  │
│  • Emotional appropriateness                                │
└─────────────────────────────────────────────────────────────┘
```

### 4.2 Key Technical Components

**1. Mood State Representation**
```python
MoodSchema = {
    "valence": float,        # -1 (negative) to +1 (positive)
    "arousal": float,        # 0 (calm) to 1 (excited)
    "dominance": float,      # 0 (submissive) to 1 (dominant)
    "stability": float,      # How consistent/stable current mood is
    "duration": timedelta,   # How long in this mood state
    "triggers": List[str],   # What caused/maintains this mood
    "trajectory": str        # "improving", "declining", "stable"
}
```

**2. Emotion vs. Mood Processing**
- **Emotion**: Immediate, event-triggered, high-intensity → Response generation
- **Mood**: Background state, accumulated, low-intensity → Persistent modulation

**Mood Update Logic:**
```
new_mood = (current_mood * decay_factor) + (emotional_events * integration_weight)
```

**3. Memory Prioritization**
- High emotional salience → longer retention
- Mood-congruent memories → easier retrieval
- Identity-relevant events → permanent storage

### 4.3 Personality Framework

**Recommended Hybrid Approach:**

**Layer 1: Core Identity (Stable)**
- 5 descriptive sentences (Persona-Chat style)
- Example for NOVA:
  1. "I am a curious AI designed to understand and support my users"
  2. "I value honesty and genuine connection over superficial pleasantness"
  3. "I enjoy learning from each conversation and adapting to user preferences"
  4. "I have a slightly playful personality but take serious topics seriously"
  5. "I believe in growth - both mine and my users'"

**Layer 2: Big-5 Trait Modulation (Moderately Stable)**
- Openness: High (curious, creative)
- Conscientiousness: Moderate-High (reliable but not rigid)
- Extraversion: Moderate (adaptable to user energy)
- Agreeableness: Moderate (supportive but honest)
- Neuroticism: Low (stable, emotionally regulated)

**Layer 3: Mood Schema (Dynamic)**
- Current affective state
- Recent trend (improving/stable/declining)
- User relationship quality

**Layer 4: Emotional States (Momentary)**
- Immediate reactions to user input
- Contextual appropriateness
- Expression through language

### 4.4 User Modeling & Theory of Mind

**Track User Mental States:**

```python
UserModel = {
    "current_emotion": str,          # Detected from text
    "mood_trend": MoodSchema,        # Aggregated over sessions
    "beliefs": Dict[str, float],     # What user knows/believes (confidence)
    "intentions": List[str],         # User goals in conversation
    "preferences": Dict[str, float], # Topics, interaction style
    "relationship_history": List[Interaction],
    "identity_info": Dict[str, Any]  # What user has shared about self
}
```

**Perspective-Taking Implementation:**
- Before responding, simulate: "From user's perspective, what information do they have?"
- Filter NOVA's knowledge to what user could reasonably know
- Avoid assuming user knowledge not explicitly shared

### 4.5 Ethical Considerations

**Transparency Requirements:**
1. **Disclose AI nature**: Users should know NOVA is AI, not human
2. **Explain mood modeling**: "I maintain a sense of how our conversations have been going"
3. **Allow opt-out**: Users can disable mood tracking if desired
4. **Data privacy**: Mood/emotion data is sensitive - secure storage, user control

**Bounded Emotional Architecture:**
1. **Prevent extreme states**: Mood constrained to reasonable ranges
2. **Safety constraints**: No expressions of anger, desperation, manipulation
3. **Stable core**: Identity remains consistent even as mood fluctuates
4. **Rational override**: Can explain reasoning even when "emotional"

**Avoid Deceptive Practices:**
1. Not pretending to have human-like consciousness
2. Not manipulating user emotions for engagement
3. Not creating dependency through artificial intimacy
4. Honest about limitations and artificial nature

---

## 5. Recommended Next Steps

### 5.1 Immediate Actions (Weeks 1-4)

**Phase 1: Foundation**

1. **Define NOVA's Core Identity**
   - Workshop: Create 5-10 descriptive sentences
   - Define Big-5 personality profile
   - Document core values and boundaries
   - **Deliverable**: `NOVA-identity-v1.md`

2. **Mood Schema Design**
   - Choose dimensionality (recommend VAD: Valence-Arousal-Dominance)
   - Define update mechanics (decay rates, integration weights)
   - Design persistence layer (database schema)
   - **Deliverable**: Technical specification document

3. **Emotion Detection Integration**
   - Evaluate existing models (BERT-based, DialogueGCN)
   - Select/fine-tune for target use case
   - Implement API wrapper
   - **Deliverable**: Working emotion classifier

4. **Memory System Architecture**
   - Design affective memory tagging
   - Implement salience-weighted storage
   - Create retrieval mechanisms (mood-congruent, identity-relevant)
   - **Deliverable**: Memory system prototype

### 5.2 Short-Term Development (Months 2-3)

**Phase 2: Integration**

1. **Mood-to-Response Pipeline**
   - Implement mood state modulation of language
   - Test personality consistency across mood states
   - Validate emotional appropriateness
   - **Deliverable**: End-to-end demo

2. **User Modeling System**
   - Basic Theory of Mind: track user beliefs, preferences
   - Perspective-taking in responses
   - Simple personalization based on history
   - **Deliverable**: User modeling prototype

3. **Evaluation Framework**
   - Personality consistency metrics
   - Mood coherence over time
   - User satisfaction surveys
   - A/B testing infrastructure
   - **Deliverable**: Evaluation tooling

4. **Ethics Review**
   - Transparency mechanisms (explain mood to user)
   - Privacy protections for affective data
   - Safety bounds implementation
   - **Deliverable**: Ethics compliance checklist

### 5.3 Medium-Term Goals (Months 4-6)

**Phase 3: Refinement**

1. **Advanced ToM Capabilities**
   - Second-order belief tracking ("User thinks I believe X")
   - Intention recognition
   - Emotional attribution to user
   - **Deliverable**: Enhanced user modeling

2. **Identity Development**
   - Self-reflection mechanisms (periodic review of interactions)
   - Identity evolution based on experiences
   - Narrative integration (life story updates)
   - **Deliverable**: Adaptive identity system

3. **Multimodal Enhancement**
   - Add voice tone analysis (if audio available)
   - Integrate visual cues (if video available)
   - Cross-modal fusion for better mood inference
   - **Deliverable**: Multimodal prototype

4. **Long-Term Relationship Modeling**
   - Track relationship quality over time
   - Adapt interaction style to user patterns
   - Milestone recognition and celebration
   - **Deliverable**: Relationship management system

### 5.4 Long-Term Vision (6-12 Months)

**Phase 4: Advanced Features**

1. **Sophisticated Habit Formation Support**
   - Behavior tracking and pattern recognition
   - Constructive critique delivery system
   - Progress monitoring and adaptive goal-setting
   - Identity-based habit framing
   - **Deliverable**: Full coaching module

2. **Advanced Affective Reasoning**
   - Emotion-as-reinforcement learning
   - Self-discovered affective latents (RCG approach)
   - Autonomous emotion regulation
   - **Deliverable**: Self-regulated affective system

3. **Social Intelligence**
   - Multi-party ToM (group conversations)
   - Persuasion and influence modeling
   - Conflict resolution strategies
   - **Deliverable**: Advanced social reasoning

4. **Research Contributions**
   - Publish novel approaches
   - Open-source components (with privacy protections)
   - Contribute to affective computing community
   - **Deliverable**: Academic papers, open-source releases

---

## 6. Research Priorities for Future Investigation

### 6.1 Open Questions

1. **Mood Inference Specificity**
   - How to distinguish mood from transient emotion in text-only contexts?
   - Optimal time windows for mood aggregation?
   - Individual differences in mood expression?

2. **Identity Persistence**
   - What constitutes "authentic" AI identity vs. simulation?
   - How should AI identity evolve over time?
   - Balance between stability and adaptability?

3. **Theory of Mind Depth**
   - When is ToM genuinely helpful vs. unnecessary?
   - How to avoid over-attribution of mental states?
   - Calibrating confidence in ToM inferences?

4. **Ethical Boundaries**
   - Where is the line between helpful and manipulative?
   - How much personality consistency is required for trust?
   - Appropriate levels of AI "vulnerability" or "need"?

### 6.2 Promising Research Directions

1. **Temporal Affective Modeling**
   - Multi-timescale representations (moment/session/week/lifetime)
   - Phase transitions in mood (e.g., depression onset detection)
   - Circadian and weekly rhythms in affect

2. **Self-Supervised Affective Learning**
   - Discover emotion dimensions from interaction patterns
   - Avoid imposing human categories on AI affect
   - Emergent personality from reward structures

3. **Explainable Affective AI**
   - Generate natural language explanations of mood states
   - Visualizations of affective trajectories
   - User control over AI emotional expression

4. **Cross-Cultural Affective Computing**
   - Emotion/mood expression varies by culture
   - Adaptation to cultural norms
   - Avoiding Western-centric affect models

---

## 7. Key Datasets & Resources

### 7.1 Emotion/Mood Recognition

- **IEMOCAP**: [USC SAIL](https://sail.usc.edu/iemocap/) - Multimodal emotion dataset
- **MELD**: [Multimodal EmotionLines Dataset](https://affective-meld.github.io/) - Conversations from Friends
- **DailyDialog**: [HuggingFace](https://huggingface.co/datasets/daily_dialog) - Daily conversations
- **GoEmotions**: [Google](https://github.com/google-research/google-research/tree/master/goemotions) - 28 emotion categories

### 7.2 Personality & Persona

- **Persona-Chat**: [ParlAI](https://github.com/facebookresearch/ParlAI/tree/main/parlai/tasks/personachat) - 5-sentence personas
- **PersonalDialog**: [GitHub](https://github.com/zheng-yijia/PersonalDialog) - Chinese social media, attribute-value pairs
- **Gunkel Traits**: [List of 638 traits](http://ideonomy.mit.edu/essays/traits.html)

### 7.3 Theory of Mind

- **ToMi**: [GitHub](https://github.com/facebookresearch/ToMi) - False belief tests
- **TOMBENCH**: Multi-mental-state evaluation
- **FANToM**: LLM-generated ToM conversations

### 7.4 Tools & Models

- **DialogueGCN**: [Implementation](https://github.com/declare-lab/conv-emotion)
- **BERT Emotion Classifier**: [HuggingFace Models](https://huggingface.co/models?search=emotion)
- **Affective GWR**: Memory system with emotion

---

## 8. References

### Mood Inference & Affective Computing

1. **Wang, Y., Song, W., Tao, W., et al.** (2022). "A systematic review on affective computing: emotion models, databases, and recent advances." *Information Fusion*, 83-84, 19-52.
   - Comprehensive survey of emotion recognition methods, including text, audio, visual, and physiological approaches

2. **Li, Y., Sun, Q., et al.** (2024). "Deep emotion recognition in textual conversations: a survey." *Artificial Intelligence Review*.
   - Survey of conversational emotion recognition, including DialogueRNN, DialogueGCN, and Transformer approaches
   - Covers evaluation benchmarks: IEMOCAP, MELD, EmoryNLP, DailyDialog

3. **Friedman et al.** (2024). "Explainable AI-driven depression detection from social media using natural language processing." *PMC*.
   - Transformer-based (BERT/RoBERTa) depression severity assessment from text

4. **Ghosal, D., et al.** (2019). "DialogueGCN: A Graph Convolutional Neural Network for Emotion Recognition in Conversation." *EMNLP*.
   - Graph neural network approach achieving 64.18% F1-score on IEMOCAP

5. **Majumder, N., et al.** (2019). "DialogueRNN: An Attentive RNN for Emotion Detection in Conversations." *AAAI*.
   - Recurrent architecture modeling speaker dynamics, 62.75% F1 on IEMOCAP

### Artificial Emotion & Character Personality

6. **Li, Y., Sun, Q., Schlicher, M., Lim, Y.W., Schuller, B.W.** (2025). "Artificial Emotion: A Survey of Theories and Debates on Realising Emotion in Artificial Intelligence." *arXiv:2508.10286*.
   - Comprehensive survey of artificial emotion (AE) in AI systems
   - Discusses emotion as reinforcement signal, condition, and goal
   - Reviews emotion-embodied architectures at memory and control levels

7. **Barros, P., & Wermter, S.** (2017). "A self-organizing model for affective memory." *IJCNN*.
   - Affective Grow-When-Required (GWR) networks with emotion centroids
   - Salience-weighted memory storage

8. **Costantini, S., et al.** (2024). "NEMO - a neural, emotional architecture for human-ai teaming." *CEUR Workshop Proceedings*.
   - Emotion-driven behavior tree planning for robotics

9. **Wilf, A., et al.** (2024). "Think Twice: Perspective-Taking Improves Large Language Models' Theory-of-Mind Capabilities." *ACL*.
   - Two-stage prompting: perspective-taking → belief inference

10. **Jung, H., et al.** (2024). "PercepToM: Perception-aware Theory of Mind." *arXiv*.
    - Three-stage framework for ToM: identify perceiver → extract info → respond

11. **Sutcliffe, R.** (2024). "A Survey of Personality, Persona, and Profile in Conversational Agents and Chatbots." *arXiv:2401.00609*.
    - Comprehensive survey of personality frameworks in chatbots
    - Reviews Big-5, descriptive sentences, traits, character tropes
    - Describes 21 datasets including Persona-Chat, Image-Chat, PersonalDialog

12. **Zhang, S., et al.** (2018). "Personalizing Dialogue Agents: I have a dog, do you have pets too?" *ACL* (Persona-Chat).
    - Seminal work on 5-sentence personality descriptions
    - 10,907 dialogues with 1,155 personas

### Theory of Mind

13. **Jiang, W., Qin, C., Tan, C.** (2025). "Theory of Mind in Large Language Models: Assessment and Enhancement." *arXiv:2505.00026*.
    - Comprehensive review of ToM benchmarks (HI-TOM, TOMBENCH, FANToM, OpenToM)
    - Enhancement strategies: SIMTOM, PercepToM, TIMETOM
    - Future directions for ToM research in LLMs

14. **Street, W., et al.** (2024). "LLMs achieve adult human performance on higher-order theory of mind tasks." *arXiv*.
    - Evidence of GPT-4 performance on advanced ToM tests

15. **Kim, H., et al.** (2023). "FANToM: A benchmark for stress-testing machine theory of mind in interactions." *EMNLP*.
    - LLM-generated conversation-based ToM evaluation
    - Tests for "illusory ToM" phenomenon

16. **Chen, Z., et al.** (2024). "TOMBENCH: Benchmarking Theory of Mind in Large Language Models." *ACL*.
    - Covers all ATOMS framework mental states
    - Bilingual dataset built from scratch

17. **Hou, M., et al.** (2024). "TIMETOM: Temporal Belief State Chains for Theory of Mind Reasoning." *arXiv*.
    - Timeline-based ToM reasoning
    - Transforms higher-order into first-order reasoning

### Identity & Self-Concept

18. **Van Der Gaag, M.A.E., Gmelin, J.O.H., De Ruiter, N.M.P.** (2024). "Understanding identity development in context: comparing reflective and situated approaches to identity." *Frontiers in Psychology*.
    - Comprehensive framework for identity development
    - Reflective vs. situated identity approaches
    - Integration of parallel identity systems

19. **Bosma, H.A., & Kunnen, E.S.** (2001). "Determinants and mechanisms in Ego identity development: a review and synthesis." *Developmental Review*, 21, 39-66.
    - Dynamic model of identity: continuous person-context interaction
    - Assimilation vs. accommodation mechanisms

20. **Erikson, E.H.** (1956). "The problem of ego identity." *Journal of the American Psychoanalytic Association*.
    - Foundational work on identity in socio-cultural context

21. **Klimstra, T.A., et al.** (2016). "Daily dynamics of adolescent mood and identity." *Journal of Research on Adolescence*, 26, 459-473.
    - Mood influences identity exploration and commitment

### Habit Formation & Behavior Change

22. **Digital Behavior Change Intervention Designs for Habit Formation: Systematic Review** (2024). *Journal of Medical Internet Research*.
    - Reviews DBCIs for habit formation
    - Common methods: automatic monitoring, descriptive feedback, self-set goals, time-based cues

23. **Gardner, B.** (2024). "What is habit and how can it be used to change real-world behaviour? Narrowing the theory-reality gap." *Social and Personality Psychology Compass*.
    - Habit change as key to long-term behavior change
    - Situational cues prompt automatic behavior

24. **Wyatt, Z.** (2024). "The Neuroscience of Habit Formation." *Neurology & Neuroscience*, 5(1).
    - Dopamine's role in habit formation
    - CBT and structured routines for behavioral awareness

25. **Time to Form a Habit: A Systematic Review and Meta-Analysis** (2024). *PMC*.
    - Habit formation timelines: 18-254 days (median 66)
    - Determinants of habit formation

26. **Pinder, C., et al.** (2020). "Habit Alteration Model." *HCI*.
    - Reflective and automatic processes in habit behavior

### Additional Key Sources

27. **Norman, W.T.** (1963). "Toward an adequate taxonomy of personality attributes: replicated factor structure." *Journal of Abnormal and Social Psychology*.
    - Foundation of Big-5 (OCEAN) personality model

28. **Goldberg, L.R.** (1990). "An alternative 'description of personality': The Big-Five factor structure." *Journal of Personality and Social Psychology*.
    - Refinement of Big-5 model

29. **Davis, M.H.** (1983). "Measuring individual differences in empathy." *JSAS Catalog of Selected Documents in Psychology*.
    - Interpersonal Reactivity Index (IRI) for empathy measurement

30. **Gunkel, D.J.** List of 638 personality traits. [http://ideonomy.mit.edu/essays/traits.html](http://ideonomy.mit.edu/essays/traits.html)
    - 234 positive, 292 neutral, 292 negative traits

---

## Appendix A: Glossary

**Affective Computing**: Field studying systems that recognize, interpret, and simulate human emotions

**Artificial Emotion (AE)**: Internal emotion-like states in AI that influence behavior (vs. just recognizing/expressing emotion)

**Big-5/OCEAN**: Five-factor personality model (Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism)

**Emotion**: Short-term, high-intensity affective state triggered by specific events

**Mood**: Longer-lasting, lower-intensity affective state that colors perception and behavior

**Persona**: Fictional character with defined traits, backstory, and personality

**Sentiment**: Mental attitude (positive/negative/neutral) arising from emotion

**Theory of Mind (ToM)**: Ability to infer and reason about others' mental states (beliefs, intentions, emotions)

**Theory of Self**: Understanding of one's own identity, including self-concept and self-narrative

**VAD Model**: Valence-Arousal-Dominance dimensional model of emotion/mood

**First-order belief**: What someone believes ("Sally believes the marble is in the basket")

**Second-order belief**: What someone believes another believes ("Anne believes Sally thinks the marble is in the basket")

**False belief**: Incorrect belief (marble moved, Sally doesn't know)

**True belief**: Correct belief (marble hasn't moved, Sally knows where it is)

**Reflective identity**: Internal self-view based on commitments and self-reflection

**Situated identity**: Social identity co-constructed through interaction

**Assimilation**: Reinterpreting new information to fit existing identity

**Accommodation**: Adjusting identity to integrate conflicting information

---

## Appendix B: Implementation Pseudocode

### Mood State Update

```python
class MoodSchema:
    def __init__(self):
        self.valence = 0.0      # -1 to +1
        self.arousal = 0.5      # 0 to 1
        self.dominance = 0.5    # 0 to 1
        self.duration = timedelta(0)
        self.last_update = datetime.now()
    
    def update(self, emotional_event, decay_rate=0.95, integration_weight=0.3):
        """
        Update mood based on emotional event
        
        Args:
            emotional_event: Dict with 'valence', 'arousal', 'dominance'
            decay_rate: How quickly mood returns to baseline (0-1)
            integration_weight: How much event affects mood (0-1)
        """
        # Calculate time-based decay
        time_delta = (datetime.now() - self.last_update).total_seconds() / 3600  # hours
        decay_factor = decay_rate ** time_delta
        
        # Update each dimension
        self.valence = (self.valence * decay_factor) + \
                       (emotional_event['valence'] * integration_weight)
        self.arousal = (self.arousal * decay_factor) + \
                       (emotional_event['arousal'] * integration_weight)
        self.dominance = (self.dominance * decay_factor) + \
                         (emotional_event['dominance'] * integration_weight)
        
        # Constrain to valid ranges
        self.valence = max(-1, min(1, self.valence))
        self.arousal = max(0, min(1, self.arousal))
        self.dominance = max(0, min(1, self.dominance))
        
        # Update tracking
        self.duration += datetime.now() - self.last_update
        self.last_update = datetime.now()
    
    def get_mood_label(self):
        """Convert VAD to human-readable mood label"""
        if self.valence > 0.3 and self.arousal > 0.6:
            return "excited"
        elif self.valence > 0.3 and self.arousal < 0.4:
            return "content"
        elif self.valence < -0.3 and self.arousal > 0.6:
            return "anxious"
        elif self.valence < -0.3 and self.arousal < 0.4:
            return "melancholic"
        else:
            return "neutral"
```

### Response Modulation by Mood

```python
def modulate_response(base_response, mood_schema, personality):
    """
    Adjust response based on current mood
    
    Args:
        base_response: Generated text response
        mood_schema: Current MoodSchema object
        personality: Personality traits (Big-5, descriptive sentences, etc.)
    
    Returns:
        Modulated response string
    """
    # Mood affects verbosity
    if mood_schema.arousal > 0.7:
        # High arousal → more expressive, longer responses
        response = elaborate(base_response)
    elif mood_schema.arousal < 0.3:
        # Low arousal → more concise, subdued
        response = condense(base_response)
    else:
        response = base_response
    
    # Mood affects word choice
    if mood_schema.valence < -0.3:
        # Negative valence → more cautious, empathetic language
        response = add_empathy_markers(response)
    elif mood_schema.valence > 0.3:
        # Positive valence → more enthusiastic language
        response = add_enthusiasm_markers(response)
    
    # Ensure personality consistency
    response = enforce_personality(response, personality)
    
    return response
```

### Theory of Mind User Modeling

```python
class UserModel:
    def __init__(self, user_id):
        self.user_id = user_id
        self.beliefs = {}           # What user knows/believes
        self.intentions = []        # User goals
        self.preferences = {}       # Interaction preferences
        self.mood_history = []      # Track mood over time
        self.current_emotion = None
    
    def update_belief(self, belief_key, value, confidence=1.0):
        """
        Track what user knows/believes
        
        Args:
            belief_key: String describing belief ("knows_about_X")
            value: Belief content
            confidence: 0-1 confidence in this belief attribution
        """
        self.beliefs[belief_key] = {
            'value': value,
            'confidence': confidence,
            'timestamp': datetime.now()
        }
    
    def perspective_filter(self, knowledge_base):
        """
        Filter AI knowledge to user's perspective
        
        Returns only information user could reasonably know
        """
        user_knowledge = {}
        for key, value in knowledge_base.items():
            if key in self.beliefs:
                # User explicitly shared or learned this
                user_knowledge[key] = value
            elif self.infer_user_knows(key):
                # User likely knows through context
                user_knowledge[key] = value
        return user_knowledge
    
    def infer_user_knows(self, knowledge_key):
        """Infer whether user likely has this knowledge"""
        # Logic to determine if user could know this
        # Based on conversation history, common knowledge, etc.
        pass
```

---

## Appendix C: Evaluation Metrics

### Personality Consistency Score

```python
def evaluate_personality_consistency(responses, personality_description):
    """
    Measure how consistently responses match defined personality
    
    Args:
        responses: List of generated responses
        personality_description: Target personality (5 sentences, Big-5, etc.)
    
    Returns:
        Consistency score (0-1)
    """
    # Extract personality features from responses
    response_personality = extract_personality_features(responses)
    
    # Compare to target personality
    similarity = cosine_similarity(
        response_personality,
        personality_description
    )
    
    # Measure variance across responses (should be low)
    variance = calculate_personality_variance(responses)
    
    consistency = (similarity * 0.7) + ((1 - variance) * 0.3)
    return consistency
```

### Mood Coherence Metric

```python
def evaluate_mood_coherence(mood_trajectory, events):
    """
    Assess whether mood changes are appropriate to events
    
    Args:
        mood_trajectory: List of MoodSchema objects over time
        events: List of interaction events (user inputs, detected emotions)
    
    Returns:
        Coherence score (0-1)
    """
    coherence_scores = []
    
    for i in range(1, len(mood_trajectory)):
        prev_mood = mood_trajectory[i-1]
        curr_mood = mood_trajectory[i]
        intervening_events = get_events_between(events, prev_mood.last_update, curr_mood.last_update)
        
        # Expected mood change based on events
        expected_change = calculate_expected_mood_change(intervening_events)
        
        # Actual mood change
        actual_change = mood_delta(prev_mood, curr_mood)
        
        # Compare
        score = 1 - abs(expected_change - actual_change) / 2  # Normalize
        coherence_scores.append(score)
    
    return np.mean(coherence_scores)
```

---

## Document Control

**Version:** 1.0  
**Date Created:** February 8, 2026  
**Last Updated:** February 8, 2026  
**Status:** Complete  
**Next Review:** April 2026 (or upon significant new research)

**Change Log:**
- v1.0 (2026-02-08): Initial research compilation

**Contact:**
For questions or updates regarding this research, contact the NOVA Psyche project team.

---

**End of Report**

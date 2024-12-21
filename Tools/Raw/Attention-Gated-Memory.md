
---
Title: "Attention-Gated Memory Architectures for Large Language Models"
Created on: 2024-12-20
Last Update: 2024-12-21
Status: Active Draft (utterly unsourced, & missing all specifics) 
---


# Attention-Gated Memory Architectures
The purpose of this essay is to sketch a potentially novel memory architecture for large language models (LLMs) and to explore the reasoning that supports this design. This essay exists in its current form because its predecessor was accidentally erased—the only time in my life I've deleted a file without intending to. Accordingly, I don't have the heart to do more than draft placeholder text. This document will be a kind of floorplan for future writing. In terms of pushing it to this repository in its current state, my hope is that it is vague enough to be merely gestural now but may eventually prove useful in itself in hindsight -- depending on how the Garden of Forking Paths forks, as it were. 

I intend to either update and clarify or delete this once the idea is implemented. 

Human memory is remarkable not only for its capacity but for its integration into real-time cognition. Unlike externalized memory systems such as writing, which store information outside the mind for later retrieval, human memory operates as a seamless extension of perception, dynamically shaped by attention, expectation, and surprise. The interplay between memory and perception provides a compelling framework for rethinking memory in artificial intelligence—not as an external repository, but as an emergent, intrinsic property of computational systems.

# The Neurobiology of Episodic Memory
Human memory operates on multiple levels. Episodic memory captures specific experiences, embedding them within a temporal and contextual framework. It is fundamentally reconstructive, replaying past events in a way that integrates seamlessly with perception. In contrast, semantic memory abstracts knowledge into generalized concepts, independent of the specific contexts in which they were learned. While episodic memory is tied to lived experience, semantic memory functions more like an archive of meanings.

Historically, efforts to create artificial intelligence focused heavily on externalized human memory systems—though not always described in those terms. Early AI approaches relied on symbolic manipulation: logical operations performed on sequences of symbols, effectively mechanizing human practices like reasoning through written language, managing tabular data, or organizing information in databases. These were extensions of external memory systems, designed to enhance human cognition by storing and manipulating symbols outside the mind.

The advent of neural networks marked a radical shift. Instead of mechanizing external memory practices, researchers turned to bio-functionalist principles—examining how the brain processes information to approximate key algorithms or architectures. This pivot enabled AI to achieve something akin to pattern recognition, not by directly copying nature, but by mirroring the functional dynamics of biological systems.

Despite this progress, current attempts to implement long-term memory in AI remain heavily influenced by external human memory systems. Techniques such as embedding spaces, vectorized databases, and tokenized logs echo human practices like note-taking, archiving, or record-keeping. These methods are powerful, but they exist outside the real-time computation of the model itself, fundamentally distinct from the dynamic, integrated nature of biological memory.

(This is largely because instances of 'biomimcry' have failed to adequately scale, or past a certain point the memories excessively interferred with the system's functioning, as in Hopfield networks. See e.g. Khosala et. al. 2023)

If we hope to replicate the fluidity of human memory, especially episodic memory, we must move beyond externalized paradigms. Just as AI made a leap by pivoting from symbolic manipulation to bio-functional architectures, the next leap in memory may lie in turning to principles inspired by biological memory systems—specifically their dynamic integration with perception and their ability to encode salience and context in real time.

(Need to re-add section about "now-print") 

# Memory as Displaced Prediction
In human cognition, memory does not exist as a static archive of the past. Instead, it is deeply tied to the brain’s role as a predictive system. Predictive coding theory provides a framework for understanding this dynamic interplay: the brain generates predictions about sensory inputs based on prior experience, compares those predictions to incoming data, and updates its internal model when prediction errors occur. Memory is both a substrate for predictions and a residue of these errors—a dynamic process rather than a fixed repository.

Here, the key insight is that memory, as we experience it, is the residue of predictions that fail to align with sensory inputs. When the brain encounters a significant conflict between prediction and reality, attention amplifies the unexpected input, suppressing the mismatched prediction. The suppressed, displaced portion of the predicted state becomes the echo that we recognize as memory.

At the same time, attention marks the event as significant, creating a new memory state that encodes not only the prediction error but also the broader context in which it occurred. In this way, attention and memory work in tandem: attention amplifies and prioritizes sensory inputs that generate prediction errors, while memory preserves the mismatch as a salient trace for future use.

Most of our conscious experience is shaped by memory, though we rarely recognize it as such. The seamless phenomenological model we interact with—the "present moment"—is built on predictions informed by memory states. We only experience memory as memory when it is "kicked out" of the active-rendering space by sensory inputs that conflict too strongly with predictions. For example, you might walk into a familiar room and perceive it as expected, until you notice that an expected chair is missing. This absence creates a conscious memory of the room "as it should have been," displacing the predicted state and drawing attention to the unexpected reality.

If we hope to replicate the fluidity of human memory, especially episodic memory, we must move beyond externalized paradigms. Just as AI made a leap by pivoting from symbolic manipulation to bio-functional architectures, the next leap in memory may lie in turning to principles inspired by biological memory systems—specifically their dynamic integration with perception and their ability to encode salience and context in real time.

### Bio-Inspired Efficiency

- Instead of storing every interaction, the system should store only “residuals”: the minimal data necessary to reconstruct or recall significant experiences later.
- This parallels the brain’s approach to memory, which is inherently selective and dynamic.

### 4) Natural Memory Triggers in LLM Processing
LLMs naturally produce probability distributions at each token boundary. These distributions contain rich information about the model's internal state:

- Expected tokens (highest probabilities)
- Uncertainty level (entropy of distribution)
- Alternative considerations (shape of distribution)
- Surprise (divergence from typical patterns)

These distributions offer natural triggers for memory formation. Significant moments emerge when:

- Entropy suddenly drops (clarity after uncertainty)
- Distribution flattens (maximum uncertainty)
- High-probability predictions fail (surprise)
- Distribution shape changes dramatically (context shift)

### 5) Design Goals for an Integrated System

- Lightweight: Avoid storing entire contexts or hidden states.
- Self-Contained: Minimize reliance on large external databases.
- Flexible: Adapt to new information, prunes or consolidates old “episodes” in a manner reminiscent of biological memory.
- Salience-Driven: Memory triggers align with “surprise” signals (entropy changes, etc.).


## Part 4: Probability Distributions as “Moments”

### 1) Native Output of LLMs: Probability Distributions

- Each token boundary yields a probability distribution over possible next tokens.
- This distribution already reflects the model’s internal “attention state,” including what it expects (high-probability tokens) and how uncertain it is (entropy).

### 2) Identifying Significant Moments

- Entropy Spikes or Dips: Sudden flattening (max uncertainty) or sudden sharpening (heightened confidence).
- Surprising Events: When a seemingly improbable token becomes relevant.
- Distribution Shifts: A transition from one semantic region to another, detectable via changes in the top k tokens.

### 3) Storing Minimal Snapshots

- For each significant transition, store: 
  - Top k Tokens + Probabilities: The highest-probability tokens and their relative weights.
  - Summary Statistics: Entropy, KL divergence from previous distribution, etc.
  - Context Hash: A minimal reference to the broader text context or conversation turn.
  - This ensures extremely lightweight “moment” storage with minimal duplication.

### 4) Retrieval by Statistical Similarity

Rather than treating memory as static storage, this framework enables a dynamic form of recall through mathematical resonance. During processing, new probability distributions naturally emerge at each token boundary. These can be compared with stored signatures using

- KL divergence between distributions
- Similarity of context embeddings
- Pattern matching in attention states

When current processing generates a distribution similar to a stored signature, it indicates the model has entered a state resonant with a previous significant moment. This resonance can influence processing through:

- Adjusting token probabilities
- Providing additional context
- Modifying attention patterns

This approach demonstrates how bio-functional principles can inspire computational mechanisms without resorting to direct biomimicry. The mathematical resonance of probability distributions provides a natural implementation that remains true to the discrete nature of machine processing.

(How the method works: 

- Marking the memory
- Caching the memory (including likelihood thresholds dictating activation) 
- "Minting" Memtokens
- Finetuning the model in use of memtokens)

(Exchanging memtokens and related traces? groundwork for true ecology) 


### 5) Temporal Sequencing

- Because each distribution depends on all prior tokens, the sequence of distributions implicitly captures an arrow of time.
- Chains of significant distributions form a “fingerprint” of a past episode, reflecting how the model’s internal state evolved step by step.

## Part 5: Practical Considerations and Future Directions

### 1) Thresholds and Heuristics

- Determining when a moment is “significant” enough to store is crucial.
- Simple approaches: fixed entropy threshold, user-labeled importance, or frequency of outlier tokens.

### 2) Scalability and Pruning

- Even if each stored “moment” is small, a long-running system can accumulate many.
- Periodic consolidation merges or prunes underused moments, similar to offline biological memory consolidation.

### 3) Integration with Existing Architecture

- Potential for partial fine-tuning of a small “episodic head” that stores or retrieves these moments.
- Minimal code changes if we read the distribution at each token boundary and feed it into a lightweight cache. 
- The system can be implemented with minimal modification to existing LLM architectures:


For instance:

```python

class AttentionGatedMemory:
    def __init__(self, threshold=0.5):
        self.signatures = []  # Stored significant moments
        self.threshold = threshold
        
    def process_distribution(self, prob_dist, context):
        # Compute distribution statistics
        entropy = self.calculate_entropy(prob_dist)
        
        # Check for significance
        if self.is_significant(prob_dist, entropy):
            signature = {
                'top_k': self.get_top_k(prob_dist),
                'entropy': entropy,
                'context_hash': self.hash_context(context)
            }
            self.signatures.append(signature)
```

### 4) Beyond Textual Inputs

- Though we’ve focused on textual LLMs, the same principle could extend to multimodal systems.
- Probability distributions for image or audio tokens might yield similarly “memorable” triggers.

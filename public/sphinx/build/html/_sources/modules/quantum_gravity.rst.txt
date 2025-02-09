.. role:: past

=============================
How We Solved Quantum Gravity
=============================

Quantum gravity has been one of the most difficult problems for physicists, up until *very recently*
:cite:`WolframAnnouncement`. This is the story from my perspective of how this discovery was made and shared in 2019 and
2020 by several scientists (including myself), who were working independently of one another.

I am *thrilled* to see the work being validated and repeated by others like Dr. Wolfram who, admittedly, have done much
more extensive and impressive work than I. I'm *very excited* to see how the world will continue to expand on this work
in the collaborative and open framework being created by Wolfram Research in the coming years!

My models are not as sophisticated as those being presented by Dr. Wolfram. However, they are arguably in the same vein.
Most interestingly, they share some interesting predictions about physical phenomena, most notably that **Quantum Mechanics
and General Relativity are the same idea!**

This wonderful result was something I saw come out of my model nearly a year ago, and is also one
of the major points made in Dr. Wolfram's announcement from earlier this week :cite:`WolframAnnouncement`!

****************
My Goals in 2018
****************

I began my graduate studies in 2018 with very lofty goals and set out to do the following:

1.   Resolve the quantum mechanics interpretations
2.   Provide the missing piece for a true theory of consciousness
3.   Solve the AI control problem
4.   Provide a protocol for control
5.   Provide a strategy for bridging m-theory and our reality by introducing higher conscious agents
6.   Justify quantum darwinism
7.   Justify the efficient simulation of quantum systems
8.   Design a graph characterization approach to identifying consciousness
9.   Develop a quantum algorithm for *fast* consciousness classification
10.  Thereby derive a functional quantum definition of consciousness
11.  Provide a technical roadmap for a *feasible* implementation of quantum conscious agents

I was strongly discouraged from trying to tackle all of this in a Masters degree. I eventually found myself switching \
into a PhD fast-track, but was still encouraged to leave the AI and consciousness related work "on the back-burner."

I settled at first with a quantum emulation project. The goal of this project was to *emulate* the behaviour of quantum
systems, specifically quantum harmonic oscillators, using commonplace electrical components. Still, this sub-project
combined control theory, machine learning, quantum mechanics, electrical engineering, software engineering,
and microchip design. It was enough to scare off almost every professor I spoke to at the university, and it looked like
I wasn't going to be able to put a committee together around it.

These are some of the things I heard as I pitched the project to the members of the Institute for Quantum Computing,
as well as the Physics and Engineering departments at the university:

.. code-block::

    "I don't think you should apply machine learning to everything."
    -- A researcher and professor of engineering

    "I can't read a single page of electrical engineering."
    -- A researcher and professor of quantum physics

    "I don't know enough about quantum mechanics."
    -- A researcher and professor of engineering

    "What you need is a mathematician."
    -- A researcher and professor of quantum physics

I was fortunate by this point to have a number of connections with inventors and entrepreneurs in the industry, who were
more open to some of my ideas. I pitched the initial emulation idea to a few industry mentors and past collaborators.

.. code-block::

    "If you think you can handle the broad interdisciplinary nature of it, go for it!"
    -- A seasoned serial entrepreneur

    "Be careful you don't give the ideas away. When you go into business, I would like to be a founder."
    -- A seasoned entrepreneur and inventor

This was my first hint that this type of work was not suited well to academia.

Encouraged at least by some of the feedback from my friends in the industry, my supervisor and I decided the project was
worth looking into. I was absolutely pumped. The committee, we thought, would come later.

I started out by trying to combine two topics I loved: quantum information theory and analog control theory. I also had
the chance to satiate my obsession with logistic maps by building a recursively evaluated logistic map into the analog
circuitry. And so, I began in earnest in September 2018.

**************************************
The Analog Electrical Quantum Emulator
**************************************

Below I include writing from my work on the analog electrical emulator from 2018 - 2019, interspersed with retrospective
comments.

|

------------

|

:past:`At the core of any quantum simulation or emulation is the idea of mapping quantum information to classical information.
At its simplest, we need each modellable quantum state to be mapped to some classical state of our classical simulation
device. Let` :math:`a \mathbb{\epsilon} \mathbb{Z}` :past:`be an integer variable. It will be the goal for this value to be
"observable", meaning that it can be measured or determined with minimal calculation and minimal deduction. This variable`
:math:`a` :past:`will be used to give each individual modellable quantum state an observable identification number.`

:past:`Consider a system with practical boundaries on the magnitude of its possible states. Let any state of the system in
question initially be assumed to be expressible using continuous variables, and modelleable by analog signals. We know
that a system matching this description is possible to engineer. As La Cour and Ott demonstrated experimentally in their
paper published in 2015` :cite:`Cour2015SignalbasedCE` :past:`, it is possible to implement a signal-based emulation of a universal qubit quantum computer.
However, they did not provide a scalable or practically useful scheme because of the evolution of the system's more complex
states in time. To produce 95 bits would require a calculation duration of roughly the age of the universe using their scheme.
So, let us assert that a viable solution must have a dependence on time that scales linearly with the complexity of the
operation. This will encourage improvement upon the design proposed by La Cour and Ott.`

:past:`Finally, a viable solution must not require the amount of hardware components or digital computing resources to scale
exponentially with the amount of modelled quantum information.`

|

------------

I was inspired by a signal-based emulation that was demonstrated in 2015 :cite:`Cour2015SignalbasedCE`, which I had
`reviewed <https://mackedweise.github.io/qemu.pdf>`_ as a class project in undergrad.

------------

|

************************************
:past:`Bandwidth Limitation Problem`
************************************

:past:`In 2015, La Cour and Ott` :cite:`Cour2015SignalbasedCE` :past:`described an implementation scheme for a signal
based emulation of general quantum computing. This model was demonstrated using analog electronics. Their scheme
introduced a mapping from quantum states to electrical analog phase representations.`

:past:`The model starts with representing the quantum state` :math:`|0>` :past:`by the in-phase and quadrature
components of an analog electrical signal. The` :math:`|0>` :past:`state is defined as` :math:`s(t)` :past:`:`

|

.. math::

    s(t) = a \cdot cos(\omega_ct) - b \cdot sin(\omega_ct) = Re[\alpha e^{i\omega_ct} ]

|

:past:`This state can be represented by a sinusoidal analog electronic signal` :math:`\alpha` :past:`.` :math:`a`
:past:`then represents the real part of the sinusoidal signal and` :math:`b` :past:`the imaginary part. The in-phase and
quadrature amplitudes can be obtained by multiplying the state by in-phase and quadrature reference signals and applying
a low-pass filter with a bandpass below` :math:`2\omega_c`:past:`.`

:past:`This can also be extended to model a general single qubit state,` :math:`s(t) = Re[\psi(t)e ]` :past:`.`

|

.. math::

    \psi(t) = \psi_R(t) + i\psi_I(t) = \alpha_0e^{i \omega t} + \alpha_1e^{-i \omega t}

|

:past:`This is a combination of the basis states` :math:`|0>` :past:`and` :math:`|1>` :past:`.`

:past:`Then we can redefine` :math:`s(t)` :past:`:`

|

.. math::

    s(t) = \psi_R (t) \cdot cos(\omega_c t) + \psi_I (t) sin(\omega_c t)

|

:past:`This achieves a way by which a general state` :math:`|\psi> = \psi (t) = \alpha`    :past:`can be modelled. The real
and imaginary parts of` :math:`\psi` :past:`serve as the in-phase and quadrature components of the carrier signal. In-phase and quadrature
references are used in the following configuration, where` :math:`\otimes` :past:`represents a 4 quadrant multiplier. A
4 quadrant multiplier circuit produces the product of its input voltages and either input voltage may be positive or
negative. The` :math:`- \frac{\pi}{2}` :past:`phase shift provides the quadrature reference, and a positive analog filter
is used to finally acquire the state` :math:`s(t)` :past:`.`

|
|

.. image:: ../_static/analog_psi.png
  :width: 250
  :alt: Analog Quantum State

|
|

:past:`Then the analog components required to represent a quantum state are: 2 analog sources, 2 quadrature multiplier
circuits, 1 phase shift circuit, and 1 bandpass filter. Similarly, n qubits with n complex coefficients can be expressed
in general using the formula:`

|

.. math::

    \psi(t) = \sum_{x=0}^{2^n-1} a_x \phi_x (t)

|


:past:`To represent such a state,` :math:`n + 1` :past:`frequencies are required; one frequency for each qubit as well
as the carrier frequency` :math:`w_c` :past:`. Such an ensemble of states can be created using an octave spacing scheme,
with` :math:`n` :past:`frequencies for the qubits, 2 frequencies for the basis states, and one for the carrier.`

:past:`Since a quantum state of` :math:`n` :past:`qubits is represented using a complex oscillating time-domain signal, the number of qubits
that can be encoded is limited by the attainable bandwidth. Another limitation to consider is the requirements for physical
components. The proposed device consists of only three types of electrical components: 4 quadrant multipliers, operational
amplifiers and analog filters. A gate uses a fixed number of multipliers, adders and inverters per qubit. La Cour and Ott claim that the total
number of components needed for the implementation of a gate scales quadratically with the number of qubits the gate
operates on. La Cour and Ott estimate that in order to achieve a density of electrical circuitry footprint
that scales exponentially with the number of qubits, transistor density would need to improve by
a factor of 1000 from what it is today. If this goal were reached, and encoding information with a 1 THz
bandwidth were possible, they claim it would then be feasible to emulate a system of 40 qubits, which is comparable to a
modern high performance computer with 1 TB of RAM.`

:past:`Due to the bandwidth limitation, the inefficiencies of this implementation largely exist in the time domain. The time
dependence of a state introduces a relationship between the signal duration` :math:`T` :past:`and number of modellable qubits` :math:`n` :past:`.
A signal duration of 10 hours would yield roughly 50 qubits, while 1 year would yield roughly 60 qubits. Even if` :math:`T` :past:`were
on the order of the age of the Universe only about 95 qubits could be represented.`

:past:`La Cour and Ott conclude that a quantum emulation device with an octave spacing of qubit frequencies would be constrained
by an exponential scaling of required bandwidth. So, this signal based emulation methodology also scales with untenable complexity.`

|

------------

In this next section, I began to formulate primitive state machines and computational modules that I thought could capture the
necessary state transitions of a computational qubit.

------------

|

*********************************************
:past:`Dual Oscillator Representation Scheme`
*********************************************

###################################
:past:`Representation Scheme Goals`
###################################

:past:`To overcome the downsides of the scheme summarized in the previous section, we will create a new scheme with the following properties:`

| :past:`1. A pair of oscillators or sinusioidal wave sources must be sufficient to emulate` :math:`n` :past:`superimposed states with the ability to be identifiably mixed or entangled`
| :past:`2. The time required to perform a measurement of a state must not scale poorly with the complexity of the state`
| :past:`3. A fixed set of hardware components must be sufficient to emulate a system of a significant number of qubits`
| :past:`4. At least as much must be knowable about an emulated quantum state as is expected to be measurable in a theoretical quantum computing system`

|

:past:`In order to build to a viable solution, we will first define the elements of the computational space in such a way that they are each representable by a single phasor.`

:past:`A probabilistic state with` :math:`n` :past:`observable values can be modelled by a probability simplex, a tetrahedron in`
:math:`n-1` :past:`dimensions. For example, in the case of a qubit, the probability of measuring a` :math:`|0>`
:past:`versus a` :math:`|1>` :past:`can be expressed as a point on a line between two endpoints. The endpoints represent
states which are 100% likely to yield an observable when measured. A line is then the geometric embodiment of the spectrum
of the probabilistic mixtures of a qubit's observable values.`

:past:`The Bloch sphere provides a more true representation of a qubit state since we know that a qubit does behave the same as a pbit.
Rather, in order to fully model a qubit, it is important to retain knowledge of the square root of its probability in a way that
is not arbitrary. Two dimensions are added on top of the probability simplex in order to account for the sign of the square root of the probability,
and for imaginary values.`

:past:`See that the imaginary component or sign of a qubit state does not affect the probability of its observable values being measured.
These characteristics do however become necessary for the application of operations represented by unitary matrices that decompose to a
combination of Pauli matrices including either` :math:`Z` :past:`or` :math:`Y` :past:`. The sign or phase flip operations do not act on
the probability dimension, which is in a sense the one most relevant to an observer.`

:past:`Consider a single qubit state in the computational basis.`

|

.. math::

    |\psi_1> = c_0|0_1> + c_1|1_1>

|

:past:`Each of` :math:`c_0` :past:`and` :math:`c_1` :past:`are complex coefficients with two terms: one real and one imaginary. We can \
rewrite the state as follows.`

|

.. math::

    |\psi_1> = \mathfrak R c_0|0_1> + \mathfrak I c_0|0_1> + \mathfrak R c_1|1_1> + \mathfrak I c_1|1_1>

|

:past:`Each coefficient in this equation for` :math:`|\psi_1>` :past:`can be broken into three pieces of information:`

| :past:`1. Whether the coefficient is real or imaginary`
| :past:`2. Whether the coefficient is positive or negative`
| :past:`3. The magnitude of the coefficient`

|

:past:`Items one and two are binary in nature, and can be captured by a bit string of binary flags. The third item, however,
exhibits a spectrum of possibilities when the observables are probabilistically mixed or entangled.`

:past:`We shall distinguish between four sets of information processors. The sum of these four subsystems will represent
a full qubit state. The first two subsystems will be responsible for maintaining information directly relevant to a measurement.
Their hardware should not be required to interact with any other subsystems in order to answer a measurement with an observable
value. The third and fourth subsystems will maintain information that is necessary to maintain about a quantum state, but not
relevant in the context of a measurement. Let the third and fourth hardware modules together be named the "flag processor module"
and each maintain two pieces of information about a term in the coefficients of each observable in a quantum state: whether it is
imaginary and whether it is negative. In the case that the entire system is maintaining a single qubit of quantum information,
then the effects of Pauli operations on each subsystem in the flag processor module can then be captured by a simple state diagram.`

|
|

.. image:: ../_static/state_machine.png
  :width: 250
  :alt: State Machine

|
|


:past:`This state machine can be described by Boolean logic and clearly lends itself to a trivial digital implementation.`

|
|

.. image:: ../_static/bool_machine.png
  :width: 250
  :alt: Boolean Logic Circuit

|
|

.. image:: ../_static/digital.png
  :width: 250
  :alt: Digital Circuit

|
|

:past:`The requirements of the digital flag processor module scale exponentially with the number of modelled qubits since
four bits are required per observable pure state. This is clearly not usable. An analog implementation of the flag processor
will also be discussed.`

:past:`The more challenging subsystems to implement will maintain the spectrum of probability between a qubit's observables.
How this is accomplished will affect how well the outcomes of measurements in our scheme will match those expected of a
true quantum computer. The probability dimension will be left to an analog electrical module, which will encode the complete
probabilistic state into two phasors.`

:past:`Keeping in mind the goal that at least as much must be knowable about an emulated quantum state as is expected to be measurable
in a theoretical quantum computing system, let us define an observable that will enable the description of qubit state
information with a pair of analog waveforms.`

:past:`Let us consider each of the first and second subsystems separately. Let each subsystem be responsible for maintaining
the magnitude of one term in each of the coefficients of each observable qubit state. Then the first subsystem might be
initialized to maintain the real terms in each of the coefficients of each observable qubit state, and the second
subsystem might be initialized to maintain the imaginary terms.`

:past:`Let each of the first two subsystems be implemented using analog electronics, and be electrically identical analog modules.`

|

------------

I sketched out a generalized state machine graph structure -- a mapping between quantum states and high dimensional
simplex geometries with weighted edges.

------------

|

###################################
:past:`Modelling Probability Space`
###################################

:past:`Since an analog module is concerned only with probability, and not sign or phase at this point, its states can be
conceptualized as points within simplexes. The simplest simplex is that of a single qubit: a line. Consider the Dirac
notation of 3 independent quantum states. The first is a state of one qubit.`

|

.. math::

    |\psi_1> = c_0|0_1> + c_1|1_1>

|

:past:`The second is a two-qubit state.`

|

.. math::

    |\psi_{1,2}> = c_0|0_1>|0_2> + c_1|1_1>|0_2> + c_2|0_1>|1_2> + c_3|1_1>|1_2>

|

:past:`The third is a three-qubit state.`

|

.. math::

    |\psi_{1,2,3}> = c_0|0_1>|0_2>|0_3> + c_1|1_1>|0_2>|0_3> + c_2|0_1>|1_2>|0_3> +

.. math::

    c_3|1_1>|1_2>|0_3> + c_4|0_1>|0_2>|1_3> + c_5|1_1>|0_2>|1_3> +

.. math::

    c_6|0_1>|1_2>|1_3> + c_7|1_1>|1_2>|1_3>

|

:past:`etc.`

:past:`The pure states of a system will correspond with the edges and surfaces of its simplex. Entangled states will exist
on the edges, and mixed states will exist inside the boundaries of the simplex. It is easy to see that the number of
observable states, and the number of vertices on the corresponding simplex is` :math:`2^Q` :past:`, where` :math:`Q` :past:`is the number of qubits.
Individually maintaining the probability of each observable being measured is not feasible. Instead, consider a point
outside of the simplex that exists in a dimension sufficiently high such that it can exist in an independent probabilistic
relationship with each pair of observables in the simplex. Its relationship with each pair of observables may be represented
by a two dimensional simplex, a triangle. This higher dimensional observable (HDO) will be bound in an relationship similar
to an uncertainty principle to the observables that form the simplex. When the HDO (conceptualized as a point) is an exact
description of the` :math:`2^Q` :past:`dimensional probabilistic state, then the probabilistic state will correspond to the point at the
dead center of the simplex. Let the HDO have a quantized number of measurable amplitudes such that each amplitude corresponds
to a unique combination of weights that the observable has in each triangular simplex it forms with each pair of the` :math:`2^Q`
:past:`dimensional simplex's observables.`

:past:`If such a geometery could be realized, the HDO would be capable of representing bounded subspaces in the` :math:`2^Q` :past:`dimensional
simplex with any width in any dimension. If this HDO were implemented in such a way that its amplitude could be measured,
then more information could be learned about a multi-qubit state than is expected of a true quantum computer. Next, a method
for achieving this geometry using analog electronics will be described.`

:past:`Consider the probability simplex for a two qubit system.`

|
|

.. image:: ../_static/2_q_simplex.png
  :width: 250
  :alt: 2 Qubit Simplex

|
|

:past:`The strengths of the HDO in its relationship with each edge will be shown in blue and red numbers. The red numbers
will be the set of strengths that conclusively identify the exact location of the probabilistic state of the qubit system.
The actual state will be included as a red dot. See that a pure observable state is trivial to identify.`

|
|

.. image:: ../_static/pure_simplex.png
  :width: 200
  :alt: Pure State Simplex

|
|

:past:`An entangled state is also trivial to identify from the strengths of the HDO.`

|
|

.. image:: ../_static/entangled_simplex.png
  :width: 250
  :alt: Entanglement Simplex

|
|

:past:`A general state on an edge requires knowledge of only two strengths of the HDO.`

|
|

.. image:: ../_static/edge_simplex.png
  :width: 200
  :alt: Edge State Simplex

|
|

:past:`Mixed states are also straight forward.`

|
|

.. image:: ../_static/mixed_simplex.png
  :width: 200
  :alt: Mixed State Simplex

|
|

:past:`The strength of the HDO with respect to an edge denoted` :math:`e_0` :past:`will be equal to an expression composed
of the distances of the state from the maximally mixed state as seen by each of the other edges that are not opposite`
:math:`e_0` :past:`. In the case of a two qubit system:`

|

.. math::

    1-(\delta e_0+\frac{1}{2}\delta e_1-\frac{1}{2}\delta e_2+\frac{1}{2}\delta e_3-\frac{1}{2}\delta e_4)

|

:past:`Let the overall strength of the HDO be 1 when its system is in the maximally mixed state. Let it be generally
true that the strength will become less as the state moves further from the maximally mixed state.`

|

------------

The next step was to encode the *exact* quantum state being represented by a point within the simplex structure
into a single numerical value that could theoretically be probed, say by a frequency measurement.

------------

|

:past:`If the HDO is to have a unique amplitude for each combination of strengths with respect to each simplex edge, then
another rule must be added. Distance from the maximally mixed state along each edge must not be treated equal. Rather,
let us choose arbitrarily that nearness to the maximally mixed state with respect to` :math:`|0^{\otimes Q}>` :past:`contributes
the most significantly to the strength. Let nearness with respect to` :math:`|1^{\otimes Q}>` :past:`contribute the least.
Let each intermediate state contribute something between these, with their contribution amount ordered according to their
binary sequence. Then continuously observing the strength of the observable in a system where the state moves gradually from`
:math:`|0^{\otimes Q}>` :past:`towards the maximally mixed state might yield a curve something like the following.`

|
|

.. image:: ../_static/strength_zero.png
  :width: 200
  :alt: Continuous Trajectory

|
|

:past:`Continuously observing the strength of the observable in a system where the state moves gradually from` :math:`|1^{\otimes Q}>`
:past:`towards the maximally mixed state would yield the following shape.`

|
|

.. image:: ../_static/strength_one.png
  :width: 200
  :alt: Continuous Trajectory

|
|

:past:`The nature of the information being encoded suggests that a quantum harmonic oscillator (QHO) may be an ideal manifestation of the HDO.
The HDO must have` :math:`n = 2^Q` :past:`observable states, which may be considered analagous to the energy eigenstates of the quantum
harmonic oscillator. Its observable states must be in superposition, like the states of the uncollapsed wave function of the QHO. We want to be
able to identify and move between each state in a hierarchy described by` :math:`a \epsilon R` :past:`, which is reminiscent of the raising and lowering operators.`

:past:`However, a QHO is not ideal for our application for several reasons. First, we want to be able to identify the precise mixture or entanglement of states,
and a QHO's wave function would collapse to an observable energy state upon being measured, making this impossible. Second, a perfect quantum harmonic oscillator
is difficult and costly to control.`

:past:`We will now endeavor to implement the HDO using electronics in a way that is inspired by the quantum harmonic oscillator but is also optimally
efficient in terms of hardware implementation. The design should also ensure that it is trivial to model the application of the Pauli matrices to the
underlying modelled lower dimensional quantum system.`

:past:`First, let the HDO be manifested as a frequency. Let the strength of the HDO be equivalent to its probability of being consistently measured by a
frequency measurement device. We will now define a hierarchy of frequencies that accomplish the actualization of this observable.`

:past:`Let` :math:`a` :past:`be a measurable integer identifier of a modelleable wave packet. Consider the parabaloid`
:math:`z_g(x,y)=gy^2+y+gx^2+x` :past:`. If we were to fix` :math:`y=0` :past:`, then this would be a parabola with a form
loosely analogous to the classical equation of potential energy in a harmonic oscillator. Imagine that`
:math:`g` :past:`might equal` :math:`\frac{m \omega^2}{2}` :past:`and the variables` :math:`x` :past:`and` :math:`y` :past:`are like position and momentum`
:math:`x` :past:`and` :math:`p` :past:`respectively.`

|

.. math::

    E = (\frac{m \omega^2}{2})x^2+(\frac{1}{2m})p^2

|

.. math::

    E_{pot} = V(x) = (\frac{m \omega^2}{2})x^2

##############################################################
:past:`The Fundamental P-Spectrum Parabaloid` :math:`z_1(x,y)`
##############################################################

:past:`Let` :math:`g=1` :past:`. Let` :math:`b \epsilon \mathbb{R}` :past:`be a real number, and the following set of
spheres to be defined in` :math:`\mathbb{R}^3` :past:`:`

|

.. math::

    \{\cup_{a=1}^{\infty} s_a: (x+ \frac{1}{2})^2 + (y + \frac{1}{2})^2 + ((z - z_1(a, b))^2 = (a + \frac{1}{2})^2\}

|

:past:`If` :math:`b` :past:`is left as a free parameter for now, this set of relations is a set of spheres that are stacked
in the shape of a parabaloid such that the minimum point in the $z$ axis of each sphere is equal to the maximum of the preceding
sphere, and each sphere is centered in the parabaloid such that it intersects the parabaloid in a circle, on a plane parallel to the`
:math:`xy` :past:`axis.`

:past:`Then the intersubsection of each circle with` :math:`z_1` :past:`will lie on the plane` :math:`z=z_1(a,b)`
:past:`. The intersubsection equation of any sphere` :math:`s_a` :past:`with the plane` :math:`y=b` :past:`is then the following:`

|

.. math::

     \sqrt{(a + \frac{1}{2})^2 - (x+ \frac{1}{2})^2 - (y + \frac{1}{2}^2)^2} + 2(b^2+b)+a^2+a+x^2+x=0

|

:past:`For each` :math:`s_a` :past:`there are four solutions to its intersubsection equation. Two of the points of intersubsection
will lie on the plane` :math:`z=z_1(a,b)` :past:`. Let this pair of points be named the "reference points". The "reference vectors"
between the center of a sphere and each of its reference points will also lie in the plane` :math:`z=z_1(a,b)` :past:`and these
vectors will have equal magnitudes.`

:past:`A sphere's other two points of intersubsection, the “data points”, will each be related to one of the sphere's reference points.
Let a "data vector" be the vector between a data point and its sphere's center. Let a "reference vector" be the vector between a reference
point and its sphere's center. Let each data point be related to a reference point such that the magnitude of the angular displacement of
each data vector from its reference vector is the same. Let this angular displacement be` :math:`\phi` :past:`. Then, each sphere will have
a unique single associated angle` :math:`\phi` :past:`. This achieves a mapping from each integer` :math:`a` :past:`to a unique`
:math:`\phi` :past:`.` :math:`\phi` :past:`, of course, could be representable by a single phasor coming from a single signal source.`

:past:`Note the similarity of our` :math:`\phi(a)` :past:`to the potential energy of the QHO` :math:`V(x)` :past:`. As the quantized real
parameter` :math:`a` :past:`increases, the frequency` :math:`\phi(a)` :past:`will increase as well.` :math:`a` :past:`can be visualized as an
integer in the x-axis. Consequently, a diagram of the energy-wise lowest-lying solutions of the Schrödinger equation of the QHO also provides a
relatively accurate depiction of our` :math:`\phi(a)` :past:`.`

|
|

.. image:: ../_static/osc.png
  :width: 400
  :alt: Quantum Harmonic Oscillator

|
|

.. math::

    H = (\frac{1}{2m})p^2 + V(x)

|

:math:`\phi(a)` :past:`is fundamentally encoded into the "data vector" that determines its frequency. Given a single data vector,
the corresponding values of` :math:`a` :past:`and` :math:`b` :past:`can be determined. We adopt a coordinate system with an origin
at the center of` :math:`s_a` :past:`similar to that of the Bloch sphere to describe the data vector, where the angle measured from
the` :math:`x` :past:`axis is denoted` :math:`\phi` :past:`and the angle measured from the` :math:`z` :past:`axis is denoted` :math:`\theta` :past:`.`

:past:`Let` :math:`b=f_2(r, \theta)` :past:`. Let` :math:`\theta` :past:`be the angle between two vectors. Let the first
vector be defined by two points: a sphere's center and its intersubsection with the plane` :math:`z=z_1(a,0)` :past:`. Let the second also be
defined by two points: a sphere's center and its intersubsection with the plane` :math:`z=z_1(a,b)` :past:`. Let` :math:`r` :past:`be the magnitude
of a data vector. Then we have:`

|

.. math::

     b=r \cdot sin(\theta)

|

:past:`Let` :math:`a=f_1(r, \phi)` :past:`. This` :math:`f_1` :past:`is simply a trigonometric transformation. Let`
:math:`z_2` :past:`be the parabolic intersubsection of the plane` :math:`y=b` :past:`with the parabaloid` :math:`z_1`
:past:`. Let` :math:`\frac{dz_2}{dx}` :past:`be the slope in` :math:`x` :past:`of` :math:`z_2` :past:`at a point approaching
a reference point on the sphere` :math:`s_a` :past:`. Then we have:`

|

.. math::

     f_1(r, \phi)=\frac{sin(\frac{\pi}{2}-dx)}{sin(\frac{\pi}{2}- asin(\frac{rsin(\phi)}{c}))}-1

|

.. math::

    c = \sqrt{2r^2-2r^2cos(\phi)}

.. math::

    dx = c sin(\frac{\pi}{2} - a sin( \frac{r sin(\phi)}{c}))

.. math::

    dz_2 = csin(\frac{\pi}{2}-dx)

.. math::

    \frac{dz_2}{dx}=2x+1=2a+1

|

:past:`It can easily be shown that $r$ is a redundant parameter in both` :math:`f_1` :past:`and` :math:`f_2` :past:`.
Any pair of reference vector and data vector are guaranteed to have the same magnitude, and the information represented
by a data vector can be inferred entirely from the angles` :math:`\theta` :past:`and` :math:`\phi` :past:`. The ratio of
both vectors’ magnitudes is always constant despite the magnitudes themselves. Therefore,`

|

.. math::

    b=f_2(\theta)=sin(\theta)

.. math::

    a=f_1(\phi)=\frac{sin(\frac{\pi}{2}-dx)}{sin(\frac{\pi}{2}- asin(\frac{sin(\phi)}{c}))}-1

|

:math:`f_2^{-1}` :past:`is trivial to define:`

|

.. math::

    \theta = f_2^{-1}(b)=sin^{-1}(b)

|

:past:`It is simple to define` :math:`\phi` :past:`as a function` :math:`f_1^{-1}` :past:`of` :math:`a` :past:`and` :math:`b`
:past:`as well. Let` :math:`T_d(a,b)` :past:`denote the data point of a sphere chosen such that` :math:`\phi` :past:`is positive. Let`
:math:`T_r(a,b)` :past:`denote the matching reference point. Then,`

|

.. math::
    \phi = f_1^{-1}(a,b) = a cos(\frac{\overline{T_r(a,b)p}
    \cdot
    \overline{pT_d(a,b)}}
        {
            |\overline{T_r(a,b)p}|
            \cdot
            |\overline{pT_d(a,b)}|
        })

|

.. math::

    p = \begin{bmatrix}
        a \\
        b \\
        a^2+a+b^2+b
    \end{bmatrix}

|

:past:`A graph of` :math:`\phi(a,1)` :past:`iteratively computed using python yields the following.`

.. code-block::

    # encodes a to phi
    def encode(a,b,g):
        radius = a + (a/(2*g))
        dz = numpy.absolute(((2*(a**2+a)-1) + numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2 - ((2*(a**2+a)-1) - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2)
        dx = numpy.absolute(a - (-1+numpy.sqrt(numpy.absolute(1-4*g*(((2*(a**2+a)-1))
        - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2 - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2))/(2*g)))
        c = numpy.sqrt(dx**2+dz**2)
        phi = numpy.arcsin(c*numpy.sin(numpy.pi - numpy.arcsin(dx/c))/radius)
        theta = numpy.arcsin(b)

    # generates states and wrties to csv
    def iterateStates(g=1):
        csvfile = open('a_{}.csv'.format(g), 'w', newline='')
        writer = csv.writer(csvfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)
        b = 0
        all_waves = []
        all_a_vals =[]
        for word in itertools.product([0,1,2,3,4,5,6,7,8,9],repeat=4):
            a_str = ''
            for bit in word:
                a_str += str(bit)
            a_val = int(a_str)
            waves = encode(a_val,b,g)
            pair = numpy.array([waves[0]])
            if((not numpy.isnan(waves[0]))):
                all_waves.append(waves[0])
                all_a_vals.append(a_val)
                writer.writerow([a_val, waves[0]])

|
|

.. image:: ../_static/a_1.png
  :width: 400
  :alt: Single Numerically Generated Curve

|
|

#########################################################
:past:`The P-Spectrum Parabaloid Family` :math:`z_g(x,y)`
#########################################################

:past:`If we return to our initial assumption that` :math:`g=1` :past:`, we can see that removing this assumption yields
a family of functions. Note that after a certain lower limit in` :math:`a` :past:`, the individual functions do not overlap.
The graph for` :math:`0<g \epsilon \mathbb{Z} \leq 6` :past:`is provided.`

|
|

.. image:: ../_static/a_n.png
  :width: 400
  :alt: Six Numerically Generated Curves

|
|

:past:`The iterative calculation of the elements of these functions demonstrates how the functions might alternatively be
interpreted as sequences. This sequential interpretation can help in the catagorization of the space of its elements.`

:past:`Each of these sequences is a Cauchy sequence. A sequence is Cauchy if`
:math:`\exists \delta > 0 : \exists n \epsilon \mathbb{N} : \forall j,k > n \: || \phi_j - \phi_k || < \delta` :past:`,
meaning that as the sequence progresses, its elements become arbitrarily close to one another.`

:past:`See that a hierarchy of frequencies` :math:`\phi(a)` :past:`has been described such that if one knows the magnitude of`
:math:`\phi` :past:`, the value of` :math:`g` :past:`will also be distinguishable, since the curves` :math:`\phi(a)`
:past:`do not overlap. Knowing both` :math:`g` :past:`and` :math:`\phi` :past:`, one may use` :math:`f_1` :past:`, a simple
trigonometric process, to deduce the value of` :math:`a` :past:`.`

:past:`If we let` :math:`g` :past:`take any real value, then the graph of` :math:`\phi(a)` :past:`becomes a vector field.
The "useful" elements of such a vector field might be determined by introducing an angular resolution` :math:`d \omega` :past:`in`
:math:`\phi` :past:`, and a maximum value for` :math:`\phi` :past:`. The number of "useful" curves in the vector field can be
found by applying the requirement that the difference in` :math:`\phi` :past:`between any adjacent points in the field is at least`
:math:`d \omega` :past:`. We can find the set of curves for which the smallest difference between adjacent points is`
:math:`d \omega` :past:`and this difference occurs near the maximum value of` :math:`\phi` :past:`.`

#########################################################################
:past:`Practical constraints on` :math:`d\omega` :past:`and` :math:`\phi`
#########################################################################

:past:`High frequency industrial electrical oscillators have ranges that reach into the tens of Gigahertz. For example,
the Axtal AXPLT2500 is a phase lock crystal oscillator product whose maximum frequency output can reach 12 GHz with a
frequency stability` :math:`\pm` :past:`3.2 ppm depending on operating conditions age, and other factors. The drawbacks
of using such a device are its physical footprint and its cost.`

|
|

.. image:: ../_static/axtal.jpeg
  :width: 250
  :alt: Axtal AXPLT2500

|
|

:past:`On the other hand, there are high frequency oscillators with ranges in the GHz that are available in common integrated
circuit chip packages, such as the $36.10 Abracon LLC product AX7MAF1-2100.0000C which outputs a maximum stable frequency of
2.1GHz at` :math:`\pm` :past:`50ppm.`

|
|

.. image:: ../_static/abracon.png
  :width: 250
  :alt: Abracon LLC AX7MAF1-2100.0000C

|
|

:past:`These devices each represent their respective families of devices: the Axtal product being a part of the family of high end,
low noise industrial oscillator products, and the AX7MAF1 being a part of the family of small footprint, highly embeddable products.
The constraints introduced by the AX7MAF1 will be analyzed since the goal is to create a cost-effective and low-profile technology.
However, the capacity of available high-end industrial tools should also be kept in mind.`

:past:`In the case that one of these oscillators is used as a frequency source for $\phi$, $d\omega$ becomes a function of the
oscillator's stability rating` :math:`s_o` :past:`and of` :math:`\phi` :past:`itself.`

|

.. math::

    d\omega(s_o, \phi) = s_o \phi

|

:past:`We will select values for` :math:`a` :past:`and` :math:`g` :past:`such that the difference between` :math:`\phi(a)`
:past:`and` :math:`\phi(a-1)` :past:`is approximately` :math:`d\omega` :past:`on the first curve that contains a value of`
:math:`\phi` :past:`that overlaps with the maximum frequency. The following code iterates through the states in a given range,
determining the number of states for each curve that can be represented within tolerance. Two device specific parameters for the
procedure are the stability and the maximum output frequency.`


.. code-block::

    # accumulator for the total number of counted states
    overall_result = 0

    # will hold the value of phi for the last state within tolerance on the previous curve
    last_phi = 0

    # starting value of g
    g = 1

    # simulation resolution in g
    d_g = 0.01

    # device specific parameters
    phi_limit = 2100000000
    osc_ppm = 50

    # data file setup
    csvfile = open('g_converging_{0}.csv'.format(g), 'w', newline='')
    writer = csv.writer(csvfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)

    # encodes a to phi
    def encode(a,b,g):
        radius = a + (a/(2*g))
        dz = numpy.absolute(((2*(a**2+a)-1) + numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2 - ((2*(a**2+a)-1) - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2)
        dx = numpy.absolute(a - (-1+numpy.sqrt(numpy.absolute(1-4*g*(((2*(a**2+a)-1))
        - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2 - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2))/(2*g)))
        c = numpy.sqrt(dx**2+dz**2)
        phi = numpy.arcsin(c*numpy.sin(numpy.pi - numpy.arcsin(dx/c))/radius)
        theta = numpy.arcsin(b)

        return numpy.array([phi,theta])

    # traverses states in tolerance
    def countStates(g, osc_ppm):
        b = 0
        all_waves = []
        all_a_vals =[]
        done = False
        i = 0
        count = 0
        while done == False:
            i = i + 1
            a_str = str(i)
            a_val = int(a_str)
            waves = encode(a_val,b,g)
            d_omega = osc_ppm*(waves[0]/1000000)
            pair = numpy.array([waves[0]])
            if((not numpy.isnan(waves[0]))):
                if((len(all_waves) == 0) or (all_waves[-1] - waves[0] > d_omega)):
                    all_waves.append(waves[0])
                    all_a_vals.append(a_val)
                    count = count + 1
                else:
                    done = True
        return count, waves[0], d_omega


    done = False
    tolerable = True

    while done == False:
        g += d_g
        result, phi, d_omega, a = countStates(g, osc_ppm)
        overall_result += result
        writer.writerow([g, phi, a, abs(last_phi - phi), d_omega])
        if (abs(last_phi - phi) < d_omega):
            print("g: {0}".format(g))
            print("phi: {0}".format(phi))
            print("d omega: {0}".format(abs(last_phi - phi)))
            print("d phi = {0} < d omega = {1}".format(abs(last_phi - phi), d_omega))
            print("num states: {0}".format(overall_result))

        elif phi > phi_limit:
            done= True
            print("g: {0}".format(g))
            print("phi: {0}".format(phi))
            print("d omega: {0}".format(abs(last_phi - phi)))
            print("phi = {0} > max phi = {1}".format(phi, phi_limit))
            print("num states: {0}".format(overall_result))
        else:
            last_phi = phi

:past:`Running the program above using the device parameters for the AX7MAF1 oscillator yields the following upper range
of curves within acceptable tolerance.` :math:`d\phi` :past:`in this chart refers to the distance between the values of`
:math:`\phi` :past:`for adjacent curves at their maximum tolerable values of` :math:`a` :past:`.`

|
|

.. image:: ../_static/abracon_tolerance_range.png
  :width: 400
  :alt: Abracon Tolerance Range

|
|

:past:`The output of the program indicated that the reason for termination was that` :math:`d\phi` :past:`had intersected with`
:math:`d\omega` :past:`, not that the maximum output frequency had been reached.`

.. code-block::

    g: 24.960000000001102
    phi: 0.9093581907426893
    d omega: 2.926448341844523e-05
    d phi = 2.926448341844523e-05 < d omega = 4.546790953713446e-05
    num states: 473498

:past:`Let the final tolerable value of` :math:`\phi` :past:`calculated by the program be called the "base frequency tolerance limit"`
:math:`L_b` :past:`. In order to stretch the vector field to fill the acceptable range of operation with usable curves, we
introduce a device specific scaling coefficient` :math:`C_d` :past:`such that` :math:`C_d \cdot L_b = \omega_{max}` :past:`,
where` :math:`\omega_{max}` :past:`is the device's maximum output frequency. Then for the AX7MAF1,` :math:`C_d \dot{=} 2309321037`
:past:`. then we define the relationship between` :math:`\omega` :past:`(the device's frequency) and` :math:`\phi`
:past:`(the angle between reference and data vectors) to be` :math:`\phi = \frac{\omega}{C_d}`.

:past:`The program can be adjusted to take this into account, spreading the curves throughout the frequency space of the device.
This will yield a higher achievable number of curves, represented in the program as the resolution in` :math:`g` :past:`.`

.. code-block::

    # accumulator for the total number of counted states
    overall_result = 0

    # will hold the value of omega for the last state within tolerance on the previous curve
    last_omega = 0

    # starting value of g
    g = 1

    # simulation resolution in g
    d_g = 0.0001

    # device specific parameters
    omega_limit = 2100000000
    osc_ppm = 50
    Cd = 2309321037

    # data file setup
    csvfile = open('g_converging_{0}.csv'.format(g), 'w', newline='')
    writer = csv.writer(csvfile, delimiter=',', quotechar='"', quoting=csv.QUOTE_MINIMAL)

    # encodes a to phi
    def encode(a,b,g):
        radius = a + (a/(2*g))
        dz = numpy.absolute(((2*(a**2+a)-1) + numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2 - ((2*(a**2+a)-1) - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2
        - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2)
        dx = numpy.absolute(a - (-1+numpy.sqrt(numpy.absolute(1-4*g*(((2*(a**2+a)-1))
        - numpy.sqrt(numpy.absolute((2*(a**2+a)-1)**2 - 4*((a**2+a)**2+1/4-(a+a/(2*g))**2))))/2))/(2*g)))
        c = numpy.sqrt(dx**2+dz**2)
        phi = numpy.arcsin(c*numpy.sin(numpy.pi - numpy.arcsin(dx/c))/radius)
        theta = numpy.arcsin(b)

        return numpy.array([phi,theta])

    # traverses states in tolerance
    def countStates(g, osc_ppm):
        b = 0
        all_waves = []
        all_a_vals =[]
        done = False
        i = 0
        count = 0
        while done == False:
            i = i + 1
            a_val = i
            waves = encode(a_val,b,g)
            omega = waves[0]*Cd
            d_omega = osc_ppm*(omega/1000000)
            pair = numpy.array([waves[0]])
            if((not numpy.isnan(waves[0]))):
                if((len(all_waves) == 0) or (all_waves[-1] - omega > d_omega)):
                    all_waves.append(omega)
                    all_a_vals.append(a_val)
                    count = count + 1
                else:
                    done = True
        return count, waves[0], d_omega


    done = False
    tolerable = True

    while done == False:
        g += d_g
        result, phi, d_omega, a = countStates(g, osc_ppm)
        overall_result += result
        omega = phi*Cd
        writer.writerow([g, phi, omega, a, abs(last_omega - omega), d_omega])
        if (abs(last_omega - omega) < d_omega):
            print("g: {0}".format(g))
            print("phi: {0}".format(phi))
            print("omega: {0}".format(omega))
            print("d omega: {0}".format(abs(last_omega - omega)))
            print("d omega = {0} < {1}".format(abs(last_omega - omega), d_omega))
            print("num states: {0}".format(overall_result))

            tolerable = False
            while tolerable == False:
                limit_g = g
                d_g_scaler = 2
                d_g = d_g*d_g_scaler
                print("adjusting dg to {0}".format(d_g))
                g += d_g
                result, phi, d_omega, a = countStates(g, osc_ppm)
                omega = phi*Cd
                if (abs(last_omega - omega) < d_omega):
                    d_g_scaler = d_g_scaler + 1
                    d_g = d_g*d_g_scaler
                    g = limit_g + d_g
                    tolerable = False
                    print("adjusting dg by adding {0} to it".format(d_g))
                else:
                    tolerable = True

        elif omega > omega_limit:
            done= True
            print("g: {0}".format(g))
            print("phi: {0}".format(phi))
            print("omega: {0}".format(omega))
            print("d omega: {0}".format(abs(last_omega - omega)))
            print("omega = {0} > max omega = {1}".format(phi, omega_limit))
            print("num states: {0}".format(overall_result))
        else:
            last_phi = phi

:past:`Running the program with the scaling factor` :math:`C_d` :past:`and a step of` :math:`dg = 0.0001` :past:`demonstrates
that 45452916 distinct, perfectly distinguishable values of` :math:`a` :past:`could be encoded into frequencies; orders of
magnitude greater than before the scaling factor was introduced. This demonstrates the effect of the device specific maximum frequency.`

.. code-block::

    g: 24.95999999995526
    phi: 0.9093581907423488
    omega: 2100000000.0495648
    d omega: 2100000000.0495648
    omega = 2100000000.0495648 > max omega = 2100000000
    num states: 45452916

:past:`This number is important since it represents the values of` :math:`a` :past:`that can be encoded with complete certainty.
The goal of this state representation scheme, however, is to represent probabilistic information in an analog signal. Therefore,
uncertainty must be introduced in a controlled manner.`

##################################
:past:`Probabilistic Measurements`
##################################

:past:`What we have done so far is to map a set of quadratic relationships to a similar set of Cauchy sequences of angular values.
We then mapped each of these sequences to a set of practically realizable frequencies. The convenience of this approach now becomes evident.
Since a quadratic relationship was chosen as the starting point, the frequency encodings we have described are also each in a sequence where
the difference between adjacent sequence terms changes linearly. Since the difference between adjacent terms in a sequence corresponding
to a value of` :math:`g` :past:`is equivalent to the difference between two frequencies that are adjacent in the` :math:`\omega` :past:`vector
field and we have guaranteed that any of 45452916 terms are perfectly distinguishable within the stability constraints of a device, we can
express the probability of measuring a particular value of $a$ in terms of only the difference` :math:`\omega(\phi(a)) - \omega(\phi(a-1))`
:past:`and the resolution of a frequency measurement device.`

:past:`Let` :math:`\sigma(a, g)` :past:`be the variance in measured values for the value of` :math:`\phi(a, g)` :past:`, and`
:math:`\delta(a, g) = \omega(\phi(a, g)) - \omega(\phi(a-1, g))` :past:`be the angular resolution of the medium maintaining
the angle` :math:`\phi` :past:`. Then the probability of measuring values of` :math:`a` :past:`and` :math:`g` :past:`can be
expressed as the following.`

|

.. math::

    p(a, g) = \frac{\sigma(a, g)-\delta(a, g)}{\sigma(a, g)}

|
|

.. image:: ../_static/p_a.png
  :width: 250
  :alt: Probabilistic Measurement

|
|

:past:`Let this probability be equivalent to the strength of the HDO. Note that a value of` :math:`a` :past:`with a particular probability
of being measured is now mappable to a specific encoding frequency. Recall that the original purpose of` :math:`a` :past:`was to enumerate modellable
quantum states. The next task is to create a mapping between each value of` :math:`a` :past:`and its corresponding quantum state such that the
probability of observing a value of` :math:`a` :past:`through measurement is equal to the strength of the HDO that exists in an individual probabilistic
relationship with each pair of observable states of the modelled qubit system.`

:past:`Recall that the greatest contributor to the strength of the HDO was chosen to be the distance
from the maximally mixed state with respect to the` :math:`|0^{\otimes Q}>` :past:`state. Therefore it is logical to assign the` :math:`g=dg`
:past:`curve to correspond to states that lie exactly between the maximally mixed state and the state` :math:`|0^{\otimes Q}>` :past:`.`

:past:`The rest of the states will be related to curves evenly spaced throughout the frequency range of the device used to maintain`
:math:`\phi` :past:`. For example, using the AX7MAF1 to model a two qubit system would yield the following "chief g curves". The spectrum will
be made to wrap back to the first state so as to better map the space inside the simplex to its curves.`

+---------------+--------------+
| chief g curve | state        |
+===============+==============+
| dg            | :math:`|00>` |
+---------------+--------------+
| 6             | :math:`|01>` |
+---------------+--------------+
| 12            | :math:`|10>` |
+---------------+--------------+
| 18            | :math:`|11>` |
+---------------+--------------+
| 24            | :math:`|00>` |
+---------------+--------------+

:past:`The system is also capable of representing states do not lie on any of the chief curves. Since`
:math:`dg` :past:`used in the simulation generating these curves was 0.0001, we know that we could use approximately 60000
curves between each of the four in the table above to represent such states.`

:past:`See that the effect of the application of an` :math:`X` :past:`gate on a qubit would be to move a state in its simplex
by reflecting it across a line that passes through the center and is orthogonal with an edge representing a transition between
two states with the operand qubit's value changing and the rest not changing, for each such edge that exists. We will partition
the curves between the chief curves with the goal of keeping this as simple as possible in practice.`

:past:`Let the intermediate curves between each chief curve be evenly divided into a number of groups called "surface groups".
Let the set of curves between a pair of chief curves be called a "vertex group", and let the lesser of the pair of chief curves
delimiting a vertex group be the "lower chief". Let there be one surface group per surface adjacent to the lower chief curve's
corresponding state in the simplex. In the case of a two qubit system, this yields surface groups of 20000 curves. Each of these
surface groups' curves will represent the strength of the observable with respect to a point on the surface correlated to its group.
Let the "vertex sum" of a surface be equal to the binary addition of the values of its vertices. Let the surface groups be ordered in`
:math:`g` :past:`according to the magnitude of their vertex sums.`

:past:`In the illustration below, each vertex group is given a color, and each surface group is labelled with a number indicating its order within its vertex group.`

|
|

.. image:: ../_static/surface_groups.png
  :width: 400
  :alt: Surface Groups

|
|

#####################################################
:past:`Conceptual Introduction to Possible Operators`
#####################################################

:past:`See that applying` :math:`X` :past:`to a qubit will move a state from one surface group to a different surface group.
The exact group transitions for a two qubit system are provided in the table below.`

+----------------+----------------------+-----------------------+---------------------+---------------------+
| operation      | operand vertex group | operand surface group | final vertex group  | final surface group |
+================+======================+=======================+=====================+=====================+
| :math:`x_1`    | :math:`|00>`         | 1                     | :math:`|10>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|00>`         | 2                     | :math:`|10>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|00>`         | 3                     | :math:`|10>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|01>`         | 1                     | :math:`|11>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|01>`         | 2                     | :math:`|11>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`2x_1`   | :math:`|01>`         | 3                     | :math:`|11>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|10>`         | 1                     | :math:`|00>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|10>`         | 2                     | :math:`|00>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|10>`         | 3                     | :math:`|00>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|11>`         | 1                     | :math:`|01>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|11>`         | 2                     | :math:`|01>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_1`    | :math:`|11>`         | 3                     | :math:`|01>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|00>`         | 1                     | :math:`|01>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|00>`         | 2                     | :math:`|01>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|00>`         | 3                     | :math:`|01>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|01>`         | 1                     | :math:`|00>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|01>`         | 2                     | :math:`|00>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|01>`         | 3                     | :math:`|00>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|10>`         | 1                     | :math:`|11>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|10>`         | 2                     | :math:`|11>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|10>`         | 3                     | :math:`|11>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|11>`         | 1                     | :math:`|10>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|11>`         | 2                     | :math:`|10>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
| :math:`x_2`    | :math:`|11>`         | 3                     | :math:`|10>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|00>`         | 1                     | :math:`|11>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|00>`         | 2                     | :math:`|11>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|00>`         | 3                     | :math:`|11>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|01>`         | 1                     | :math:`|10>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|01>`         | 2                     | :math:`|10>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|01>`         | 3                     | :math:`|10>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|10>`         | 1                     | :math:`|01>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|10>`         | 2                     | :math:`|01>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|10>`         | 3                     | :math:`|01>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|11>`         | 1                     | :math:`|00>`        | 3                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|11>`         | 2                     | :math:`|00>`        | 2                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+
|:math:`x_{1,2}` | :math:`|11>`         | 3                     | :math:`|00>`        | 1                   |
+----------------+----------------------+-----------------------+---------------------+---------------------+

:past:`In general, a NOT gate applied to all qubits will be achievable as a reflection across the center of the`
:math:`g` :past:`curve spectrum. A NOT gate applied to a single qubit is equivalent to two operations. First, a shift to
the vertex group that has an order that differs from the original vertex group's order by the weight of the operand qubit's
position in the binary interpretation of the state. This is achievable by adding the weight of the operand qubit's position
to the order of the vertex group and allowing the vertex group order to wrap around 0. Second, The state must be shifted to
a new surface group of an order that can be determined by "reflecting" the original surface group order across a number
corresponding with the order of the qubit being operated on. See that in the case of a two qubit system, when the first
qubit is operated on we reflect the surface number across the value "1" to get the new surface number. When the second qubit
is operated on, we don't need to reflect its surface number at all since it is the highest order qubit.`

|

.. math::

    (1, 2, 3)

|

:past:`These ideal properties of the NOT gate can guide us in defining the complete mapping from simplex to` :math:`g`
:past:`curve spectrum, which is a projection of a 3D space to 2D. It also demonstrates how simple the identification of an
operation might be for an observer. In the two qubit system, a` :math:`X` :past:`gate or similar operation can be easily recognized by
simply partitioning the entire set of possible modellable our states into 12 surface groups. For more complex operations, the number of
partitions required might increase. However, complete knowledge of the operand and output of a Pauli operator in our probability space
will not be ultimately required to identify the Pauli operation that took place. We will see how this can be taken advantage of by a
support vector machine in the subsection on deep learning state tomography.`

:past:`It should be clear that applying a NOT gate will be trivial to accomplish in the frequency domain. the actual implementation
of this operation will be detailed later. Applying` :math:`I` :past:`is equivalent to a NOP, and both phase and sign flips will be
accounted for in the flag processor. Therefore, the only operation we still fundamentally need to support is a change of the magnitude
of the state coefficients of the modelled quantum system.`

:past:`Only real valued multipliers will be considered here. We expect that multipliers will be applied to pure states like`
:math:`|0>` :past:`or` :math:`|1>` :past:`and will be used mainly in state preparation. We will start with a number of qubits
in the maximally mixed state. For example,`

|

.. math::

    |\psi_{1,2}> = \frac{1}{2}|0_1>|0_2> + \frac{1}{2}|1_1>|0_2> + \frac{1}{2}|0_1>|1_2> + \frac{1}{2}|1_1>|1_2>

|


:past:`Then multiplying a pure state by a number greater than 1 will shift the probabilistic state towards the multiplied state.
Multiplying a pure state by a number less than 1 will shift the probabilistic state away from the multiplied state. The nearness
of a mixed state to a pure state can be determined from its frequency representation since the frequency yields $g$ and $a$, which exactly
indicate the position of the state in its simplex space. If the original mixed state is in on a chief curve, then a multiplication simply
shifts the state higher in` :math:`a` :past:`. Otherwise if it is in the vertex group of the chief curve, it shifts the mixed state both up in`
:math:`a` :past:`and towards the chief curve in` :math:`g` :past:`. If the original state is on a curve in another vertex group, then the state
will shift higher in` :math:`a` :past:`and towards the targeted chief curve in` :math:`g` :past:`. Both the change in magnitude and NOT
operations will described in detail shortly.`


#################################################################################
:past:`Capabilities and Limitations of the Dual Oscillator Representation Scheme`
#################################################################################

:past:`Since roughly 240000 individual` :math:`g` :past:`curves are achievable using the AX7MAF1, we can be confident that`
:math:`Q=\frac{log(240000)}{log(2)} \dot{=} 18` :past:`qubits can be maintained using two analog modules, without limitation
on interaction between the qubits, entangling or otherwise. However, a further optimization can be applied in order to reach 20 qubits.`

:past:`The maintainable probability precision between any two observables is related to the number of maintained` :math:`g`
:past:`curves divided from the number of maintained states.`

|

.. math::

    precision = \frac{100}{2 \cdot 189.38715 \cdot (\frac{45452916}{240000})} \dot{=} 0.264\%

|

:past:`If we were comfortable with maintaining states to a probabilistic precision of 1%, we might introduce a number of additional
"secondary` :math:`g` :past:`curves" and "tertiary` :math:`g` :past:`curves" by partitioning each original` :math:`g` :past:`curve
into three sets of values. Let every` :math:`a` :past:`value satisfying` :math:`a` :past:`mod` :math:`3 = 0` :past:`remain unchanged, every`
:math:`a` :past:`value satisfying` :math:`a` :past:`mod` :math:`3 = 1` :past:`be assigned to a secondary` :math:`g` :past:`curve and
every` :math:`a` :past:`value satisfying` :math:`a` :past:`mod` :math:`3 = 2` :past:`be assigned to a tertiary` :math:`g` :past:`curve.
Then, the size of each primary` :math:`g` :past:`curve will drop to` :math:`4 \cdot 0.264\% \dot{=} 1.056\%` :past:`. An additional
secondary and tertiary curve with the same precision will be considered to exist and represent space in a simplex close to the primary`
:math:`g` :past:`curve -- space that the next primary` :math:`g` :past:`curve would have previously been considered to represent.
This would enable us to stretch the device to approximately model 20 qubits.`

:past:`Interestingly, 20 qubits is the number given by La Cour, Ott, Starkey and Wilson in their paper as the practical amount of
qubits possible to maintain on a single chip as well.`

:past:`In general, our relationship between qubits and probability precision becomes:`

|

.. math::

    precision = 1\% \cdot 2^{Q - 20}

|

**********
References
**********

.. bibliography:: references.bib
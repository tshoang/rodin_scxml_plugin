Proof of INV @container_active
==============================

s a non−root state, 
   and either (1) s is active but none−exiting state, OR
              (2) s is an entering state
then
  either 
 (G1) the container of s is active but none−exiting state, OR
 (G2) the container of s is an entering state

Since s is a non−root state, there exists a region r containing s·

Proof−by−case
(1) s is active but none−exiting state
   − We first prove that s is NOT an enabling state by contradiction, i·e·, assuming that s is an enabling state·
     + by instantiating @enabling−unique_exiting_states_in_a_region, we obtain that s is the unique exiting state in r,
     this is in contradiction with (1) that s is a non−exiting state·
   − We proceed by proving (G1) by proving 
       (1−1) the container of s is an active state
       (1−2) the container of s is a non−exiting state
     
    (1−1) This follows from invariant @container_active, stating that if a state is active then its container is active
    (1−2) We prove this by contradiction, i·e·, assuming that the container of s is an exiting state·
      − Instantiating @exiting−contained_region∈ Since container(s) is an exiting state and contains region r, 
        there must be an exiting state in r, let's call this state x·
      − Instantiating exiting−either_one_or_all_in_a_region, since x is an exiting state in r, either 
           (1−2−1) x is the unique exiting state in r, OR
           (1−2−2) all states in r are exiting states
        We proceed by prove−by−case
        (1−2−1) If x is the unique exiting state in r
            − Instantiating @exiting−unique_enabling_states_in_a_region, x is the unique enabling state in r·
 
            − We prove that x is NOT an active state· 
              This is because in each region there can be at most one active state (invariant @active−region−unique)
              In region r, s is the active state (due to (1)) and 
                  must be different from x as s is a non−exiting state and x is an exiting state
            − x is an enabling state and according to the guard of the event, all enabling states must be active hence contradiction
  
        (1−2−2) all states in r are exiting states, it is a contradiction as s is in r but s is a non−exiting states·

(2) s is an entering state
    Consider 2 cases
    (2−1) container of s is also an entering state ⇒ hence we have (G2)
    (2−2) container of s is NOT an entering state
        - instantiating @entering−stay_within_state, since
			   entering(trf) ∩ r ≠ ∅ ∧ <−−− TRUE because s is an entering state
			   entering(trf) ∩ container[r] = ∅ <−−− This is because of (2−2)
   		so the container of s is enabling but NOT exiting state
        - Since all enabling state has to be active the transformation to occur,
           it means that the container of s is active but none−existing state (G1)


Proof of INV @content_active
==============================
 For all s where 
      (H1) s is a container state and
       s is (H2·1) active and NOT exiting state OR
            (H2·2) s is an entering state
  then
      there exists a child state of s which is either
       (G1) active and NOT existing state OR
       (G2) an entering state

Consider proof by cases for (H2·1) and (H2·2)

(H2·1), i·e·, s is active and NOT exiting state
  − Instantiate INV @content_active, we have
    there exist a child state of s which is active, call this child state x
  − Consider proof by case on x is an exiting state OR ¬
    (a) x is an exiting state
        + We first prove that there exists a child state of s which is an entering state
           −− There exists a region r contains x
              ==== TBA ====
           −− r ◁ container=r × {s}, i.e., every state in r must have
          s as its container.
              === TBA ===
           −− Instantiating @entering−you_must_go*somewhere with r, we
           obtain that there must be an entering state within r
        + Let's call this child state x0, which is an entering state·
           x0 is a candidate for (G2)
    (b) x is NOT an exiting state
        x would be a candidate for (G1)
 
(H2·2) i·e·, s is an entering state
   − There exists a region r contained in s, i·e·, ∃ r   · r∈regions ∧r ◁ container=r × {s}
          ==== TBA ====
   − Instantiate AXM @entering−contained*region,
       we obtain that there is an entering state in r, i·e·, entering(trf) ∩ r ≠ ∅
       we call this entering state in r x and 
       we will prove that x is a candidate for either (G1) OR (G2)
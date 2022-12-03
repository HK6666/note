Relational Design Theory（没搞懂是什么）

为了避免冗余和更新异常问题：
• 将关系 U 分解成几个更小的关系 Ri
• 其中每个 Ri 与其他 Rj 的重叠最小
• 通常，每个 Ri 包含关于一个实体的信息（例如，雇员、
部， ...）

Amstrong’s Axioms & Inference Rules（或许是考试重点）

(F1) Reflexivity If X ⊇ Y, then X →Y
(F2) Augmentation X → Y ⇒ XZ → YZ
(F3) Transitivity e.g. X → Y, Y → Z ⇒ X → Z
(F4) Additivity (or Union) X → Y, X → Z ⇒ X → YZ
(F5) Projectivity (or Decomposition) X → YZ ⇒ X → Y, X → Z
(F6) Pseudotransitivity X → Y, YZ → W ⇒ XZ → W
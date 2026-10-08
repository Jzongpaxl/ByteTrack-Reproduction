# ByteTrack Reproduction Notes

## 🛠️ Environment Stack
* **Python**: 3.10.x
* **PyTorch**: 2.6.0+cu124
* **GPU**: RTX 4060 / CUDA
* **NumPy**: 1.23.5 (Pinned for compatibility)

---

## 🐛 Compatibility Issues & Fixes

### Issue 01: NumPy 2.x Attribute Error (`np.float`)
* **Symptom**: 
  Running the official ByteTrack code threw an `AttributeError: module 'numpy' has no attribute 'float'` during tracker initialization.
* **Root Cause**: 
  The original ByteTrack codebase uses `np.float` in `yolox/tracker/byte_tracker.py`. This attribute was deprecated in NumPy 1.20 and completely removed in the modern NumPy 2.x ecosystem.
* **Resolution**: 
  Instead of refactoring or tampering with the original research source code, we pinned the environment's dependency to a compatible older version:
  ```bash
  pip install numpy==1.23.5
  Verification:
Reran the official demo script to successfully verify tracker initialization and inference pipeline.

Engineering Takeaway:
When reproducing legacy research code, prioritize environment/dependency compatibility management over modifying source logic to preserve original experimental integrity.

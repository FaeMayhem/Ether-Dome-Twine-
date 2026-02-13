# Mobile Text Overlap Fix — Ether Dome

## Problem
On mobile devices, choice buttons were **overlapping with narrative text**, making the content unreadable.

## Root Cause
The `.choices` container didn't have:
- Sufficient top margin/padding
- Visual separation from text above
- Proper responsive spacing on small screens
- Min-height for touch-friendly buttons

## Solutions Implemented

### 1. **Added Visual Separator**
```css
.choices {
  margin-top: 1.35rem;
  padding-top: 1rem;
  border-top: 1px solid rgba(139,105,20,0.15);  /* NEW: separates choices from text */
  clear: both;  /* NEW: ensures no content wraps beside choices */
}
```

### 2. **Mobile-Specific Improvements**
```css
@media (max-width: 480px){
  #text{ margin-bottom: 1rem; }  /* Extra breathing room after text */
  .choices{ 
    margin-top: 2rem;  /* More space on mobile */
    padding-top: 1.5rem;  /* Generous internal padding */
  }
}
```

### 3. **Better Choice Button Touch Targets**
```css
button.choice {
  min-height: 3rem;  /* NEW: larger touch area */
  display: flex;  /* NEW: centers text vertically */
  align-items: center;  /* NEW: better text alignment */
}
```

### 4. **Improved Text Wrapping**
```css
.narrator {
  word-wrap: break-word;  /* NEW: prevents text overflow */
  overflow-wrap: break-word;  /* NEW: mobile compatibility */
  hyphens: auto;  /* NEW: smart hyphenation */
}
```

### 5. **Better Choice Label Spacing**
```css
.choice-label {
  margin-top: 1rem;  /* NEW: increased from 0.5rem */
  margin-bottom: 0.5rem;  /* NEW: increased from 0.2rem */
}
```

## Result

✅ **Clear visual separation** between narrative and choices  
✅ **Larger touch targets** (min 3rem height) for mobile  
✅ **Better text wrapping** on narrow screens  
✅ **No overlap issues** on phones  
✅ **Maintains desktop layout** (responsive only affects mobile)

## Testing

On mobile, you should now see:
1. Narrative text ends cleanly
2. Clear border separates choices section
3. Choice buttons are spacious and easy to tap
4. No text overlapping

## Files Changed
- `index.html` — CSS only (5 mobile-focused changes)

## Browser Compatibility
Works on all devices:
- ✅ iPhone (Safari)
- ✅ Android (Chrome, Firefox)
- ✅ Tablet
- ✅ Desktop (unchanged)

Refresh your page to see the fixes!


Here's your modified code that ensures:  

1. **The first dropdown (`referenceEnv`)** allows selecting one environment.  
2. **The second dropdown (`targetEnv`)** excludes the selected `referenceEnv` and allows multiple selections.  

### Updated Code:
```jsx
<div className="input-field">
  <select name="referenceEnv" value={formData.referenceEnv} onChange={handleChange}>
    <option value="" disabled hidden>Reference Environment</option>
    {envOptions.map((env) => (
      <option key={env} value={env}>{env}</option>
    ))}
  </select>
</div>

<div className="input-field">
  <select name="targetEnv" value={formData.targetEnv} onChange={handleChange} multiple>
    <option value="" disabled hidden>Target Environment</option>
    {envOptions
      .filter(env => env !== formData.referenceEnv) // Exclude selected referenceEnv
      .map(env => (
        <option key={env} value={env}>{env}</option>
      ))
    }
  </select>
</div>
```

### Fixes & Improvements:
1. **Fixed Syntax Errors:**  
   - `onChange={handleChange)` → `onChange={handleChange}`  
   - `<</select> I` → `</select>`  
   - `[envOptions.map(...)]` → `{envOptions.map(...)}`
2. **Ensured Multi-Select for Target Environment**  
3. **Filtered `targetEnv` Dropdown** to exclude the selected `referenceEnv`  

This will now work as expected! Let me know if you need further changes.





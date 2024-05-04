# Google Search Keyword Copy Bookmarklet

This bookmarklet allows you to copy search terms or keywords from Google while typing in the search box. It automatically copies the keywords to your clipboard when they are visible.

## How to Use

1. **Create a new bookmark**: Right-click on your browser's bookmarks bar and select "Add Page" or "Add Bookmark".
2. **Name the bookmark**: Give it a descriptive name, like "Google Keyword Copy".
3. **Paste the code**: In the URL field, paste the following code:

```javascript
javascript:(function() {    const suggestions = [...document.querySelectorAll('.lnnVSe')];    if (suggestions.length > 0) {        const searchTerms = suggestions.map(suggestion => suggestion.getAttribute('aria-label')).filter(Boolean);        if (searchTerms.length > 0) {            const output = searchTerms.join('\n');            const textArea = document.createElement('textarea');            textArea.value = output;            document.body.appendChild(textArea);            textArea.select();            document.execCommand('copy');            document.body.removeChild(textArea);            alert('Copied ' + searchTerms.length + ' autosuggest terms to clipboard!');        } else {            alert('No autosuggest terms found.');        }    } else {        alert('No suggestions elements found. Make sure the autosuggest box is visible.');    }})();

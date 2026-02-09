# Order Matcher Pro Edition 🚀

A powerful, browser-based order processing tool that automatically matches customer orders with your master product database.

## ✨ Features

- **Smart Product Matching**: Fuzzy search with priority-based ranking (customer-specific > master list)
- **CSV/XLSX Import**: Load your product database from Excel/CSV files
- **Customer Autocomplete**: Quick customer selection with suggestions
- **Interactive Verification**: Modal-based confirmation for ambiguous matches
- **Dual Output Formats**:
  - ClickUp-friendly order lists
  - Invoice details table with SKUs and pricing
- **Unit Conversion**: Supports KG, SM, Units, PKT and more
- **No Backend Required**: Runs entirely in the browser

## 🚀 Quick Start

1. **Open the app**: Simply open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)

2. **Load your database**:
   - Click "Choose File" to upload your product database (CSV/XLSX format)
   - Database should contain: Customer, Product, SKU, Price columns

3. **Process orders**:
   - Select a customer from the autocomplete dropdown
   - Paste your order text
   - Click "PROCESS EVERYTHING"
   - Verify matches in the interactive modal
   - Copy the ClickUp output or view invoice details

## 📁 Database Format

Your CSV/XLSX file should include these columns:

| Column Name | Description | Example |
|-------------|-------------|---------|
| Customer | Customer name (use "master" for general stock) | "Acme Corp" |
| Product | Full product description | "Premium Pepperoni 500g" |
| SKU | Product code | "PEP-500-RED" |
| Price | Unit price | 12.99 |

**Sample entry:**
```
Customer,Product,SKU,Price
Acme Corp,Premium Pepperoni 500g,PEP-500-RED,12.99
master,Basic Pepperoni 1kg,BAS-PEP-1KG,8.99
```

## 🎯 How It Works

### Matching Priority
1. **Customer-Specific** - Products from the exact customer
2. **Master List** - Products marked as "master", "stock", or "general"
3. **All Others** - Products from other customers (lowest priority)

### Processing Flow
```
Raw Order Text → Split Lines → Extract Qty/Unit → Fuzzy Match → 
Priority Sort → Interactive Verification → Final Output
```

### Search Logic
- Removes extra spaces and splits search terms
- Requires ALL search terms to match
- Uses Levenshtein distance for similarity scoring
- Displays top 20 matches with priority tags

## 💡 Usage Tips

### Order Text Format
The parser understands multiple formats:
- `2 x Premium Pepperoni`
- `3kg Basic Salami`
- `10 units of Cheese Slices`
- `5 pkt Smoked Ham`

### Quick Actions
- **Keep As Text**: Use original line when no match is found
- **Ignore Line**: Skip problematic lines entirely
- **Manual Search**: Type in modal to find specific products

### Keyboard Shortcuts
- **Enter** in modal: Accept selected suggestion
- **Escape**: Close modal
- **Click outside**: Close dropdowns

## 🛠️ Technical Details

### Built With
- **SheetJS/xlsx**: Client-side spreadsheet parsing
- **Vanilla JavaScript**: No frameworks required
- **Modern CSS**: Grid layout, flexbox, CSS variables

### Browser Compatibility
- Chrome 60+
- Firefox 55+
- Safari 11+
- Edge 79+

### File Support
- CSV files (comma-separated)
- XLSX (Excel 2007+)
- XLS (Excel 97-2003 via SheetJS)

## 📊 Output Examples

### ClickUp Format
```
ORDER FOR: Acme Corp
2 KG x Premium Pepperoni 500g
10 Units x Cheese Slices 200g
5 PKT x Smoked Ham 1kg
```

### Invoice Table
| SKU | Product | Qty | Price |
|-----|---------|-----|-------|
| PEP-500-RED | Premium Pepperoni 500g | 2 KG | 12.99 |
| CHS-200 | Cheese Slices 200g | 10 Units | 8.50 |

## 🐛 Troubleshooting

### Common Issues

**"Database Ready" not showing**
- Ensure your file has proper column headers
- Check browser console for errors (F12 → Console)
- Try a simple CSV file first

**No customer suggestions**
- Verify "Customer" column exists in your file
- Customer names shouldn't be "master", "stock", or "general"

**Products not matching**
- Check spelling in your order text
- Verify products exist for the selected customer
- Use manual search in the modal for tricky items

**Modal not showing suggestions**
- Type at least 2 characters in the search box
- Try broader search terms (e.g., "pep" instead of "pepperoni")

## 🔒 Privacy & Security

- **100% Client-side**: All processing happens in your browser
- **No Data Upload**: Files never leave your computer
- **No Tracking**: No analytics or telemetry
- **Session Only**: Data clears on page refresh

## 📞 Support

Found a bug or have a feature request?
- [Open an Issue](https://github.com/Die-virus/order-matcher-pro/issues)

---

**Pro Tip**: Save your frequently used databases locally for quick access. The system doesn't store data between sessions for security.

## 📄 License

This project is open source and available under the MIT License.

# Final replacement of all problematic Unicode characters with ASCII-safe characters
fully_ascii_safe_content = (
    ascii_safe_content
    .replace("—", "-")
    .replace("™", "")
    .replace("…", "...")
    .replace("•", "-")
)

# Regenerate the PDF with the fully cleaned content
pdf = FPDF()
pdf.add_page()
pdf.set_auto_page_break(auto=True, margin=15)
pdf.set_font("Arial", size=10)

for line in fully_ascii_safe_content.split('\n'):
    pdf.multi_cell(0, 10, line)

# Save to file
final_output_path = "/mnt/data/Sovereign_Declaration_HMV_Final.pdf"
pdf.output(final_output_path)

final_output_path

# Simple HTML Averages Selector

Built by Claude Sonnet 5 (Medium), free account version.<br>
Source code is yours to modify as you see fit. Changes will not be accepted, please fork.<br>
Below is the conversation that built this app.<br>

---

**User:**

Hello Claude. I need a simple html web app.
In the yellow boxes are inputs that you can type whole numbers into. It'll be the range from between the first number up to the second number. Both ranges need to be filled - do nothing if only one or neither are not filled. They must be integer values only.
When they are filled, then that's where the green space comes into play. Populate the green space with the blue boxes that display the total numbers in sequence between the two input numbers, including the two input numbers.
The blue boxes will be buttons that can be clicked one or many times. When clicked, add the button's value to a list. Automatically calculate the average of the list, meaning that if I click one blue box and then click another, the value of each clicked blue boxes are added together and divided by 2 since I chose two boxes.
Populate the green box reasonably, only display up to 10 blue boxes in a single row before moving down to the next row. If a row contains less than ten boxes then stretch the widths of the blue boxes evenly to fill the total width of the green box.
Display a non-intrusive list of numbers in the purple box. The number list should be each chosen number, separated from each other visually and in line with the theme. They can be lighter in "opacity" or be using color values that kind of blend in with the background, as long as they are distinctly visual. Keep the displayed numbers like the green box, ten to a row and populating downward. Center align then, but keep the spacing between the appearing numbers the same (no need to stretch across).
The reset button should only reset the total average to the default state, not reset the yellow input boxes or the filled blue boxes in the green box.
The image shows an example of the layout I'm looking for. Do not use the colors in the final layout, it is only to assist you with what I'm envisioning for the layout. Center align the page, and give it a modern dark mode theme.

---

**Claude:**

A few notes on how it behaves:

- The range inputs only accept whole numbers (typed digits, optional leading `-`); if either is empty or non-integer, the board is left untouched and a small red hint appears for invalid entries.
- The blue number buttons re-render only when the actual range changes, so your selections and average won't get wiped just from re-typing the same range.
- Clicking a number adds it to the running list — click it again and it's added again, updating the average live.
- The purple-equivalent box shows selections in soft, low-opacity monospace chips, 10 per row, centered.
- Reset only clears the selections/average — your range inputs and populated board stay put.

*[file was presented]*

---

**User:**

Bring the background color of the selected numbers closer down to the background color of the page, it's too much like the buttons area.

---

**Claude:**

Darkened the picks box down to `#0d0f15`, much closer to the page background, so it no longer reads as another panel like the button board.

*[file was presented]*

---

**User:**

Remove the border line of the selected numbers space, and reduce its numbers per row from 10 down to 3.
What's your opinion on the layout, do you think it might work if it were a two-column layout? Title remains at the top, reset button under it. The range input, average display, and the selected numbers display on the left side and everything else on the right? The right side should take up the majority of space in this case, of course.

---

**Claude:**

Both done — border's gone and the picks list now wraps at 3 per row.

On the two-column idea: I think it works well, actually better than the current single-column stack. Here's why:

- The left column (range inputs, average, selected numbers) is all "state" — small, text-driven, doesn't need horizontal room. Giving it a narrow column stops the average number and the range inputs from feeling lost in a sea of width they don't need.
- The right column (button board) is the one thing that actually benefits from width — more room means fewer wrapped rows and bigger, easier-to-click buttons, especially once someone types a big range.
- It also creates a nice interaction logic left-to-right: inputs and results on the left, the "work surface" on the right. That mirrors how a lot of calculator/config tools are laid out (controls left, canvas right).

One thing to watch: the left column will have very different content heights depending on state — right after reset it's short (just an input row and a dash), but once someone's picked 15+ numbers the picks list will grow tall and could end up taller than the button board on a small range. I'd cap the picks box with a max-height and let it scroll internally so the left column doesn't stretch the whole page or throw off vertical alignment with the right column.

Want me to go ahead and build that layout?

*[file was presented]*

---

**User:**

Yes, go ahead and build the layout. No need to add a scroll or cap, just allow the numbers to infinitely add rows to the bottom - the use case for this selector is minimal and will probably not exceed a block of nine selections.

---

**Claude:**

Now let's left-align the sidebar content (range row, average block) since it's no longer centered under a wide page, and add a responsive collapse for narrow screens.

Done. Layout is now: title + reset centered up top, then a two-column row below — a narrow left sidebar (range, average, selected numbers) and a wider right column (button board). The picks list keeps growing downward with no cap, and it collapses back to a single centered column on narrow screens.

*[file was presented]*

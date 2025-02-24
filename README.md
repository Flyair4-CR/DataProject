# DataProject
# code for question 4
tables=soup.find_all("table")
gme_table=tables[1]

rows = tesla_table.find_all("tr")
data = []

for row in rows:
    cols = row.find_all("td")
    cols = [col.text.strip() for col in cols]
    if cols:
        data.append(cols)

gme_revenue = pd.DataFrame(data, columns=["Date","Revenue"])
gme_revenue["Revenue"] = gme_revenue['Revenue'].str.replace(',|\$', "", regex=True)

# code for question 6
make_graph(gme_data, gme_revenue, "Gamestop")

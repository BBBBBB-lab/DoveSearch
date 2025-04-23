from flask import Flask, request, render_template
from safe_search_filter import is_safe_query  # hypothetical filter function

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')  # the above HTML

@app.route('/search')
def search():
    query = request.args.get('q')
    if not is_safe_query(query):
        return "Sorry, that search term isn't allowed on DoveSearch."
    results = fetch_safe_results(query)  # hypothetical function to fetch safe search results
    return render_template('results.html', results=results)

if __name__ == '__main__':
    app.run(debug=True)

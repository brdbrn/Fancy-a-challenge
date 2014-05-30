Fancy-a-challenge
=================

A little challenge that we put to some applicants


Instructions

This is an initial code test that we will build upon in future rounds.
At this stage this should be a simple test that should take ~ 15m to complete.
In your code, carefully consider the time/memory complexity of your solution. Strive for performant code that is still extensible and easy to reason about.
Background

Qubit has a network of HTTP servers in multiple datacenters that receive  HTTP requests from our client’s websites in real time. On an average day, these servers process over a billion requests per day (hence the focus on performance).
For instance, when on http://www.johnlewis.com/ you will see somethine like the following GET request:
http://pong.qubitproducts.com/t2?vn=3.23.5&id=johnlewis&cid=b20524ae-befe-11e3-b335-425861b86ab6:b20527e2-befe-11e3-b335-425861b86ab6&pid=hu0zjubjo51eiu&tid=hu0zjpwncy664dpw&t=1397553972084&ping=0&v=%7B%7D&pnum=1&ont=0&sc=%5B2%2C0%5D&ct=1&bt=0&url=http%3A%2F%2Fwww.johnlewis.com%2F&ref=
As part of this programming task, you will be working on a library that can use data from the http request logs for computing metrics. Specifically, to count the number of unique visitors currently active on a given url (for example, http://www.johnlewis.com/ or http://www.johnlewis.com/electricals/ipad-tablets/c600002154).
Stage 1

We want to roll out a new feature to count the number of visitors on a given url using the stream of incoming HTTP requests (as seen above). A very crude means to do this is to count the number of distinct visitors seen on a url since the beginning of the day (12 AM).
Clickstream data will be provided to you in JSON format, this will be the input to your code.
Sample message (json):
{
    "userid": "b20524ae-befe-11e3-b335-425861b86ab6:b20527e2-befe-11e3-b335-425861b86ab6",
    "url": "http://www.espncricinfo.com/county-cricket-2014/engine/match/692721.html?cluster=undefined;view=comparison;wrappertype=none;xhr=1#cricketlive",
    "type": "GET",
    "timestamp": 1360662163000
}
userid: A unique ID representing the user
url : The url the visitor has accessed
type: The HTTP method used to access the URL
timestamp: The timestamp for when the action occurred
As part of your solution, your code should implement an Interface Aggregator of the form:
    public interface Aggregator {
        public void process(String d);
        public Long getUrlCount(String url);
    }
If your code makes assumptions about the incoming data, be sure to make this clear in documentation provided with your solution.
Submitting your solution

Bundle your code into a single tarball, ensuring that your code compiles with JDK 7.

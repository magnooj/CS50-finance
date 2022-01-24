# C$50 Finance

In this guide we want to implement a website via which users can “register”, “login” “buy” and “sell” stocks, like below:

<img src="https://github.com/magnooj/CS50-finance/blob/main/static/1.png?raw=true" alt="Picture of dashboard">

## Background

If you’re not quite sure what it means to buy and sell stocks (i.e., shares of a company), head [here](https://www.investopedia.com/articles/basics/06/invest1000.asp) for a tutorial.

We’re about to implement C$50 Finance, a web app via which you can manage portfolios of stocks. Not only will this tool allow us to check real stocks’ actual prices and portfolios’ values, it will also let you buy and sell stocks by querying [IEX](https://iextrading.com/developer/) for stocks’ prices.

Indeed, IEX lets you download stock quotes via their API (application programming interface) using URLs like `https://cloud.iexapis.com/stable/stock/nflx/quote?token=API_KEY`.

Before getting started on this project, we’ll need to register for an API key in order to be able to query IEX’s data. To do so, follow these steps:

- Visit iexcloud.io/cloud-login#/register/.
- Select the “Individual” account type, then enter your email address and a password, and click “Create account”.
- Once registered, scroll down to “Get started for free” and click “Select Start” to choose the free plan.
- Once you’ve confirmed your account via a confirmation email, visit (https://iexcloud.io/console/tokens).
- Copy the key that appears under the Token column (it should begin with `pk_`).
- In a terminal window execute:

``` bat
export API_KEY=value
```

where `value` is that (pasted) value, without any space immediately before or after the `=`. You also may wish to paste that value in a text document somewhere, in case you need it again later.

## Install requirements

This guide wrote for Windows Terminal and if you have another OS you may change it. 

Before we start, you should clone this [GitHub repo](https://github.com/magnooj/CS50-finance) and then install the dependencies.

``` bat
git clone https://github.com/magnooj/CS50-finance.git
cd CS50-fincance
pip install -r requirements.txt
```

## Through the files

Now, we are ready to run and test our project. By running `ls` you can see these files:

- [`app.py`](https://github.com/magnooj/CS50-finance/blob/main/app.py) : The APIs
- [`finance.db`](https://github.com/magnooj/CS50-finance/blob/main/finance.db) : Database of users and transactions
- [`helpers.py`](https://github.com/magnooj/CS50-finance/blob/main/helpers.py) : Some helpers algorithms
- [`requirements.txt`](https://github.com/magnooj/CS50-finance/blob/main/requirements.txt) : Required packages 
- [`/static/`](https://github.com/magnooj/CS50-finance/static/) : Favicon and CSS files
- [`/templates/`](https://github.com/magnooj/CS50-finance/templates/) : All the HTML files we needed to run this app that includes `jinja` codes in them.

### ***Flask API***

The first step in building APIs is to think about the data we want to handle, how we want to handle it and what output we want with our APIs. In our example, we want users can register, log in, log out and buy, sell and qout stocks; Finally, see the history of their transactions.

The main HTML file in our app is `layout.html`. We created a template that other HTML files cand extend that. 

In this example, we create Flask eight routs so that we can serve HTTP traffic on that route.

- `/` or `index` : Is the homepage of our app. If user loged in, it display the user’s current cash balance along with a grand total (i.e., stocks’ total value plus cash). But, if user didn.t log in, it displays the login page.
- `register` : It has a form that user can register by filling it.
- `buy` : In this route, users can input a stock’s symbol and buy some shares.
- `sell` : In this page, users can `SELECT` from theis stocks’ symbol and sell their shares.
- `qoute` : Users can lookup the price each share in a stock’s symbol.
- `history` : It displays an HTML table summarizing all of a user’s transactions ever, listing row by row each and every buy and every sell.
- `login` and `logout` : These routes start and terminate user’s session.

Of course there is some files like `apology.html` that displays the error to the user. You can check other files.

Now, We cheked our files and sqw how our app is working. To run the app, when you are in `CS50-finance` directory, enter this command in the terminal:

``` bat
flask run
```

I hope you enjoyed how to stocks' exchange web application using flask. if you have any comments please do not hesitate to send me an [e-mail](mailto:magnooj@gmail.com).

Regards,

Ali Ganjizadeh

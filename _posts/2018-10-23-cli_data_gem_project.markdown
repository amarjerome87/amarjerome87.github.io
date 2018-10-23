---
layout: post
title:      "CLI Data gem Project"
date:       2018-10-23 22:24:36 +0000
permalink:  cli_data_gem_project
---


My CLI data gem project scrapes baseball players names and biography from https://www.britannica.com/list/10-greatest-baseball-players-of-all-time.  The majority of the project was relatively straightforward with manageable kinks at various points. However, iterating through the scraped data and isolating what I needed was a challenge. 

doc = Nokogiri::HTML(open("https://www.britannica.com/list/10-greatest-baseball-players-of-all-time"))
    list_doc = doc.css("ul") #container ul
    list_doc.collect.with_index do|li,i|
      player = self.new
      player.name = doc.css("h2")[i].text.scan(/[A-Z][a-z]+/)
      player.name = player.name.join(" ")
      player.summary = doc.css("p")[i].text
      player
    end
  end
    
    Iterating with .each caused a type issue which prevented me from manipulating the data as an array. I then switched to collect without an index but I the players were no longers listed numerically. Finally, I switched to collect with index and was able to operate on the data and numerically list the players. 

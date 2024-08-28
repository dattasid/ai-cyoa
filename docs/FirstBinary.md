As a first attempt, I create a basic game similar to the earliest choose your own adventure books. Each page will offer 2 choices, with each choice often having wild and random consequences. The story was loose and unfocused, which is something AI can do very well.

The AI is given the basic premise of the story (eg: this is a space adventure) and then left to craft the story on its own. AI is instructed to write 1-2 paragraphs of the story, then offer 2 options to the player. As a next step, I pick up each option and append it to the story, then ask the AI to continue the story.

Because the large number of calls needed (say 100 calls per game) I am limiting myself to cheap models, (at keast until I know my code and method works), which might be the reason for low quality results. For now I have used Mixtral 8x22B .

We need 10-12 steps to get a satisfying story. However, fully expanding all options to 12-12 steps will lead to exponential number of pages (2^10=1024 pages). I noticed that in the books I read, some branches end very quickly and suddenly with usually bad, sometimes good endings. There are only a few narrative arcs that continue over many pages and offer fleshed out stories. To emulate this, I decided to drastically and randomly prune the full 2^10 pages. I tried to make sure there is at least 1 branch which will go the full 10 steps, and many others will end suddenly.

Results:

1. The AI did remarkably well for space adventures. While sometimes stuck in boring situations, it did often shift to new scenes like exploring an alien outpost or responsing to a distress signal. Ai was ok with changing the scene by itself every couple pages pages.
2. Because there is no overarching structure and branches are not aware of each other, the stories can diverge very fast. Eg: You can go to a alien outpost. Then choose to  go in or explore outside. If you go in, you can spend years studying the alien technology. If you explore outside, the planet may suddenly explode.
3. When I reach a pruned node, I instruct the AI to end the story here. I even choose a ending (good or bad) and ask AI to follow through. This did not go well.
  1. In the best case AI was able to wrap up the story. In the worst case AI ignored instructions and just continued the story.
  2. Since the pruning came without warning, the story was often in the middle of something and was not ready to end. This could be why the AI refused to end in many cases. When ended, it was very sudden and abrupt. Eg: go from a dialog scene to rush through conclusion and solving the final mystery in 2 sentences.
  3. For sci-fi, it kind of works as it is similar to the books I read, where you sometimes randomly and abruptly reached dead ends.
  4. Things still kinda worked for scifi but went poorly for fantasy.
5. this method worked much more poorly for fantasy. This because AI needed many more pages to properly conclude a scene. This caused the random pruned ends to be much more abrupt, with the AI often refusing to end the story.
6. If I used a fantasy story premise generated in ChatGPT, 

# TPP-notebook
some problem of learning tpp, just a note

2024.9.8 [metetpp](https://github.com/BorealisAI/meta-tpp)+[lightning-hydra-template](https://github.com/ashleve/lightning-hydra-template)
1.In metatpp, idk why author use the pyrootutils and delete the ".project-root" file, the second is the point, because i first run the metatpp demo, it dosen't work, and keep pop the error: "FileNotFoundError: Project root directory not found. Indicators: ['.project-root']", well, i thought it was sth that need to be generated, so i backe to the lightning-hydra-template demo, well, just "python src/train.py" it worked perfect，so at fist time i thought it was pyrootutils package problem, so i change the metetpp code train.py base on lightning-hydra-template train.py using the rootutils instead of pyrootutils, failed,but the error changed, it work out in first few info but stop at the ModuleNotFoundError: No module named 'nfe'. So here is the second problem: how to install nfe, i didn't realize the need of setup.py for install own package. By that time ,actually i was quite close to the success, even i dnk why, but all i need is to find out how to install package, but unfortunatly i thought it was still the FileNotFoundError problem which cause this package problem, so i undo everything, make the code back to origianal status. 
2.Strat from beginning, finally idk why but i check the folder structure, found a misssing  ".project-root" file which exist in lightning-hydra-template but not in metatpp, i checked it in github, almost a n empty file, i copyed it into local code, the second problem showed again:ModuleNotFoundError: No module named 'nfe', now we backed to how to install package, i check the code of nfe in github, find out it need whole git to install package instead of a nfe folder, well, that was pretty easy to solve, download, install, third problem poped out  UnicodeDecodeError: 'gbk' codec can't decode byte 0x80 in position 2348: illegal multibyte sequence, i made a mistake here, i change the code of setup.py to encoding="gbk", which should be "uthf8",actually utf8 should be deafult, so the error info confused me, of course, the change didn't work, about three times i realized it should be encoding="utf8",i changed it worked. Then the forth error 'sklearn' PyPI package is deprecated, use 'scikit-learn' rather than 'sklearn' for pip commands.First meet, but easy, change the sklearn to scikit-learn in setup.py just like it said in error.Finally, the right error lightning.fabric.utilities.exceptions.MisconfigurationException: No supported gpu backend found! which means all i need is a gpu, the code should be fine.

Summary:
1.add ".project-root" file
2.download [neural-flows-experiments(nfe)](https://github.com/mbilos/neural-flows-experiments) put it in src/models/tpp/flow
3.change the decode to UTF8(optional)
4.install nfe

the von neumann architecture uses
- [[ram]]
- arithmetic logic unit (ALU)
- control unit
- [[register]]
- [[input output]]
- executes programs using the [[fetch-execute-cycle]]
![[neumann architecture.png]]
- the von neumann architecture is kind of an implementation of a turing machine
- it contains instructions on how to build a general purpose computer
- **von neumann original paper**: https://web.mit.edu/sts.035/www/PDFs/edvac.pdf
# harvard architecture
- the von neumann architecture uses the ram to store both the data and the instructions
- the harvard architecture uses a rom (read-only memory) chip to store the instructions and ram to store the data
- the differences are:
	- harvard architecture can fetch both data and instructions at the same time
	- harvard architecture can not rewrite the instructions
- because of these fundamental differences:
	- harvard architecture is good for embedded systems
	- von neumann is good for commercial computers
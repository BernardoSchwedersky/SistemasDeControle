.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1],[1,1])
		plt.clf()
		#ag,phase,omega = control.bode(G,Hz=True,dB=True,margins=True,color='k') 
		ag,phase,omega = control.bode(G,Hz=True,dB=True,color='k') 		
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exemploBodeD.png')
		
.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1,5],[1,11,10])
		plt.clf()
		#ag,phase,omega = control.bode(G,Hz=True,dB=True,margins=True,color='k') 
		ag,phase,omega = control.bode(G,Hz=True,dB=True,color='k') 		
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exemploBodeE.png')
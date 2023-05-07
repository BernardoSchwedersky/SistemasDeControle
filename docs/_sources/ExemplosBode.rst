	
.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([15],[1,9,20,12])
		plt.clf()
		#ag,phase,omega = control.bode(G,Hz=True,dB=True,margins=True,color='k') 
		ag,phase,omega = control.bode(G,Hz=True,dB=True,color='k') 		
		plt.xlabel("Frequência (rad/s)")

		plt.savefig('source/figures/exemploBodeA.png')
		
		
.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([15],[1,9,20,12])
		plt.clf()
		mag,phase,omega = control.bode(G,Hz=True,dB=True,margins=True,color='k') 
				
		plt.xlabel("Frequência (rad/s)")

		plt.savefig('source/figures/exemploBodeB.png')
		
		
		
		
.. container:: toggle, toggle-hidden

	.. exec_code:: realCTsignals signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt
		import control

		G = control.tf([1],[1,10,0])
		plt.clf()
		#ag,phase,omega = control.bode(G,Hz=True,dB=True,margins=True,color='k') 
		ag,phase,omega = control.bode(G,Hz=True,dB=True,color='k') 		
		plt.xlabel("Frequência (rad/s)")
		plt.savefig('source/figures/exemploBodeC.png')
		

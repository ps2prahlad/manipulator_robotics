# manipulator_robotics
%5 dof robotic manipulator complete robot with 180 degree constraints user defined control.

%open the directory in matlab and then




%(1) run , startup robo file

%for forward kinematics use following codes

dh=[0 0 0.75 0;0 0 0.15 1.571; 0 0 0.5 0; 0 0.72 0.12 1.571; 0 0 0 0];
r=SerialLink(dh);
r.fkine([0.2 0.2 0 0.3 0 ]);
r.plot([0.2 0.2 0 0.3 0]);

r.teach;





%for inverse kinematics

 mdl_puma560;
p560.plot(qz);
T=transl(0.6,0.1,0)*rpy2tr(0,180,0,'deg');
q=p560.ikine6s(T);


%for motion
syms th1 th2 th3 th4 th5;
r.fkine([th1 th2 th3 th4 th5]);
for th1=0:.1:pi/2
   r.plot([th1 0 0 0 0]);
   pause(.25)
end
 

# test1

Collection of MATLAP codes for implementing cascade algorithm
For more information, please see the publication: Identification of critical connectors in the directed reaction-centric graphs of microbial metabolic networks

Last update: 2019-04-10
This repository is administered by Sung Ho Yoon (syoon@konkuk.ac.kr), Department of Bioscience and Biotechnology, Konkuk University, Seoul 05029, Republic of Korea
Installation
Required Software:
•	A functional Matlab installation (R2015a or higher).
Required MATLAL code file:
•	in_degrees.m : For calculating the in-degree of each node
•	cascade.m : For calculating the cascade set of a given node
Example data file:
•	directed_adjacency_matrix_of_ecoli_reaction_graph.mat : Adjacency matrix of the reaction graph converted from the metabolic network model of E.coli (iJO1366) in Matlab format
•	rxn_list.mat : Reaction list of the E. coli reaction graph corresponding to the adjacency matrix in Matlab format
% Examples of calculating cascade numbers with matlab codes
% Start Matlab
% Locate two files, "in_degrees.m" and "cascade.m", in the same folder and set working directory to the foler in matlab.

[Example 1] toy model in the paper "Identification of critical connectors in local connectivity and between modules in the directed biological network" 
% 1-1. To get a cascade number of a specific node: 
% Execute the following in the command window in Matlab
G = zeros(7,7);
G(1,2)=1; G(1,3)=1; G(1,4)=1; G(2,4)=1; G(3,4)=1; G(4,5)=1; G(5,6)=1; G(6,7)=1; G(7,6)=1;
affected_nodes = cascade(G,1)
cascade_number=length(affected_nodes)
 
% 1-2. To get all the cascade numbers of all nodes: 
% Execute the following in the command window in Matlab
list_of_cascade_number=zeros(1,7);
for i=1:7 
	affected_nodes = cascade(G,i);
	list_of_cascade_number(1,i)=length(affected_nodes);
end 
list_of_cascade_number

[Example 2] To get the list of the cascade numbers of all nodes of the reaction graph converted from the metabolic network model of E.coli (iJO1366). 
% Execute the following in the command window in Matlab
load('rxn_list.mat');
load('directed_adjacency_matrix_of_ecoli_reaction_graph.mat')
list_of_cascade_number=zeros(1,1251);
for i=1:1251	
	affected_nodes = cascade(ijo1366_diadjBIG3,i);
	list_of_cascade_number(1,i)=length(affected_nodes);
end 
list_of_cascade_number

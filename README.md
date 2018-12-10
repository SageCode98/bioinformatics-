# bioinformatics-
bioinformatic python, SQL and R studio code 
SQL code to creat and edit Genbank table 
-> CREATE TABLE genes (
-> ProteinID varchar(15),
-> Product varchar(200),
-> Gene varchar(100),
-> Start char(8),
-> Stop char(8),
-> locus_tag varchar(20),
-> translation varchar(2000)
-> );

SELECT statement to return just the thrB gene.
select Gene from genes where Gene= 'thrB';
SELECT statement to return all three genes which starts with 'thr'
mysql> select Gene from genes where gene like ('thr%');
SELECT statement to return all genes whose start site falls between base 2500
and 5000.
select * from genes where start >2500 and start<5000;
INSERT statement that could have been used to add thrB (all fields).
insert into genes values ('ACB01208.1','Homoserine kinase','thrB',2801,3733);


biotest database

Number of entries in the organism table:
SELECT COUNT(*) FROM organism;

   
SELECT statement which queries the locus ID and product for all genes which contain the word 
'lyase'.
SELECT locus_ID , product from genes where product like '%lyase%';


Query for the locus ID, start and stop coordinates for all genes which have a start 
coordinate between 10,000 and 50,000.
SELECT locus_ID , start , stop from genes where start>10000 and start<50000;


 single query which
returns all gene rows with the following two columns:   Locus ID, G
SELECT locus_ID , genus FROM genes join organism on genes.org_id=organism.id ;

Python
basic python functions:

#!/usr/bin/env python3
r = 7.5
pi = 3.1415
circumference = 2*pi*r
print "circumference:" , circumference

x = pi*r
print "r:" , r
print "pi:" , pi
print "x:" , x


p="10"
t="7"
q="70"
string_test = "{0}X{1}={2}"
print(string_test.format(p,t,q))

dna = 'ATGGAACCAACGTCAGTGACTTCGTCAG'
print "The lenght of your sequence is:" , len(dna)

print "The first codon is:", dna[:3]

count_motif = dna.count("AA")
print "There are",count_motif, "instances of the motif'AA':" 



#!/usr/bin/env python3
program that prints all the numbers from 1 to 100, inclusive, each on its own line. 
x = 1
while x <=100:
        print(x)
        x = x + 1
        
Start a script with the following line:
counts = '8,3,6,2,12,5'
Transform this comma-separated string into a list using the split() function.  The program should take each 
element of that list in turn and divide it into 48 (i.e. 48/element) and print the result of the division, like this:
48 / 8 = 6.0

counts = '8,3,6,2,12,5'

result = list(map(int, counts.split(',')))

for x in range(0, len(result)):
        print ('48/%s='%(result[x]),48/result[x])
        

function called start_codon which accepts a DNA sequence as its argument and returns the first 
codon as a string. 

start_codon = raw_input(" Enter DNA sequence: ")

print(start_codon[:3])

Script to count the number of sequence entries within this file and report the count like:

F = open("e_coli_k12_dh10b.faa","r")
test_string = F.read() 
print ("There were", test_string.count(">gi") ,"sequences within the file")

F.close()

fasta_sequence_count = raw_input(" Enter Sequence: ")
print ("There were",fasta_sequence_count.count(">gi") ,"sequences within the file")

#!/usr/bin/env python3

import re 

pattern = re.compile('bc*')

text12 = '''abccccccccccccccccccccccccccccccccccccccccccdefghijklmnopqrstuvwxyz
ABCDEFGHIJKLMNOPQRSTUVWXYZ \*\*\*\*\***\*\*\****** regular expressions 
0123456789   b b b b 
'''
Whatever ='ABC240ABC-444ABC-947ABC0'

matches = pattern.finditer(text12)

for match in matches:

        print(match)

pattern1 = re.compile('\\+\**')

matches1 = pattern1.finditer(text12)

for match in matches1:

        print(match)

pattern2 = re.compile('\D\D\D\d+\D\D\D[-]\d+\D\D\D')

matches2 = pattern2.finditer(Whatever)

for match in matches2:

        print(match)

pattern3 = re.compile('\b\w{5}')

matches3 = pattern3.finditer(text12)

for match in matches3:

        print(match)


F = open('users.txt.',"r")
contents = F.read()

who_pattern = re.compile('^\w*')

where_pattern = re.compile('pts/\d+')

when_and_IP_pattern = re.compile('\d\d\d\d[-]\d\d[-]\d\d\s\d\d[:]\d\d\s[(]\w*\W\w*\W\w*\W\w*[)]?\W(\d\d\d|\d\d)?(\W)?(hsd1|nyc|win)?(\W)(md|res|ad)?(\W)?(comcast|rr|jhu)?(\W)?(net|com|edu)?(\W)?')

who = who_pattern.finditer(contents)
where = where_pattern.finditer(contents)
when_and_IP = when_and_IP_pattern.finditer(contents)

length = len(who)
for x in range(0,length):
 print(who[x],'on',where[x],'at',when_and_IP[x])


#print ('%son%sat%s'%who,where,when_and_IP)

  

word= ('boy, girl, sister, brother, the pain I feel, town, house townhouse')
words= word.split(",") 
count = 0
lenght= len(words)
for i in range(0,lenght):
        if re.search('[aeiouAEIOU]',words[i], flags=re.I):
                count=count+1;
                        if count >=2 :
                                print("has vowels")
                                        break
else:
        print(" doesnt have vowels")




 vowels in words:
        if words == (vowels[0],[1],[2],[3],[4])

                print (vowels[0][1])

teststring = "this is a test,string"
pattern = re.compile(\w+(\s*),\w+(\s*)
words= pattern.finditer(teststring));
word = sords.split(",")

print(word)
(END) 



biopython edited modules:
#!/usr/bin/env python3



from Bio.Alphabet import IUPAC

from Bio.SeqUtils.ProtParam import ProteinAnalysis

from Bio import SeqIO

from operator import itemgetter


amino_acids = ('A','R','N','D','C','Q','E','G','H','O','I','L','K','M','F','P','U','S','T','W','Y','V')

handle = open("e_coli_k14_dh10b.faa","rU")
length_file = SeqIO.parse(handle, "fasta")
count = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
percentage = [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]

for record in SeqIO.parse(handle, "fasta",IUPAC.protein):
        seq = record.seq.tostring()
        analysed_seq = ProteinAnalysis(seq)
        D =  analysed_seq.count_amino_acids()
#       print (D)
#       print (D.keys())
#       print (D.values())

        listval = [D.get(key, 0) for key in amino_acids]
#       print(listval)
        for i in range (0,20) :
                count[i] = count[i] + listval[i]

        #C =  analysed_seq.get_amino_acids_percent()
        #print (C)


summation = sum(count)
for k in range(0,20):
        #print(count[k])
        multiply = count[k]*100
        percentage[k] = multiply/float(summation)

test_list=list(zip(amino_acids,count))
#print(test_list)
#print (summation)


#print(percentage)

#sorted_values=sorted(test_list)
sorted_values=sorted(test_list,key=itemgetter(1))
#print (sorted_values)
sorted_percentage = sorted(percentage)

for j in range (15,20) :
        print (sorted_values[j],sorted_percentage[j])

#print (sorted_values)






(END) 




Object oriented programing:
module
#!/usr/bin/python3
import random
class healthRecord(object):
        patient_first_name = 'John'
        patient_last_name = 'Miller'
        patient_BP = ''
        sys=0
        dia=0
        patient_health = 'Good'


        def change_last_namex(self,last_name):
                self.patient_last_name=last_name
        def set_health_record(self):
                sys = random.randint(70, 180)
                dia = random.randint(40, 100)
                record=str(sys) +'/' + str(dia)
                self.patient_sys=sys
                self.patient_dia=dia
                self.patient_BP=record

        def get_BP(self):
            return self.patient_BP
        def get_health(self):
            if (self.sys >= 100 and self.sys <120):
               if (self.dia >=70 and self.dia <=80):
                  self.health='good'
               else:
                  self.health='bad'
            else:
               self.health='bad'
            return self.health
module1.py (END) 


#!/usr/local/bin/python3
from module1 import healthRecord
p = healthRecord() 
print ('Health reacord for  '+ p.patient_first_name + p.patient_last_name)
p.change_last_namex("papa")
print ('Health reacord for  '+ p.patient_first_name + p.patient_last_name)
p.set_health_record()
print ("patient record after updating:")
r=p.get_BP()
print('patient BP is' + r)
q=p.get_health()
print(q)
#print ('patient has' + p.gethealth() + 'blood pressure') 
pythoncode_script1 (END) 


R studio code 
data query data 
library("biomaRt")

ensembl = useMart("fungal_mart", dataset='scerevisiae_eg_gene',host="fungi.ensembl.org")

getBM(attributes=c('entrezgene','external_gene_name','name_1006','go_linkage_type'), filters='go', values= 'GO:0006623', mart=ensembl) 
End.


data query for Clinvar SNPs:
getBM(attributes = c('refsnp_id','refsnp_source','chrom_start','chr_name','chrom_end','translation_start','translation_end','consequence_type_tv','sift_prediction','polyphen_prediction'), 
filters = c('chr_name'), 
values = list(1), 
mart = snpmart)




















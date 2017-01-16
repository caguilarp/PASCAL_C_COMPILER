Se debera clonar el presente proyecto, solo es permitido trabajar en C/C++, una vez finalizado se deberan subir los cambios al repositorio actual, la gramatica a utilizar es la siguiente.

pascal-program: 
   program identifier program-headingopt ; block . 


program-heading:  
   ( identifier-list ) 


identifier-list: 
   identifier  
   identifier-list , identifier  


block:  
   block1  
   label-declaration ; block1  


block1:  
   block2  
   constant-declaration ; block2  


block2:  
   block3  
   type-declaration ; block3  


block3:  
   block4  
   variable-declaration ; block4  


block4:  
   block5  
   proc-and-func-declaration ; block5  


block5:  
   begin statement-list end  


label-declaration:  
   label unsigned-integer  
   label-declaration , unsigned-integer  


constant-declaration:  
   const  identifier = constant  
   constant-declaration ;  identifier = constant  


type-declaration:  
   type  identifier = type  
   type-declaration ;  identifier = type  


variable-declaration:  
   var variableid-list : type  
   variable-declaration ; variableid-list : type  


variableid-list:  
   identifier  
   variableid-list ,  identifier  


constant:  
   integer  
   real 
   string
   constid  
   + constid 
   TADD- constid 


type:  
   simple-type  
   structured-type  
   ^ typeid  


simple-type:  
   (  identifier-list )  
   constant ... constant  
   typeid  


structured-type:  
   array [ index-list ] of type  
   record field-list end  
   set of simple-type  
   file of type  
   packed structured-type  


index-list:  
   simple-type  
   index-list , simple-type  


field-list:  
   fixed-part  
   fixed-part ; variant-part 
   variant-part 


fixed-part:  
   record-field 
   fixed-part ; record-field 


record-field: 
   empty 
   fieldid-list : type   


fieldid-list:  
   identifier  
   fieldid-list ,  identifier  


variant-part: 
   case tag-field of variant-list 


tag-field: 
   typeid  
   identifier : typeid  


variant-list:  
   variant 
   variant-list ; variant 


variant: 
   empty 
   case-label-list : ( field-list )  


case-label-list:  
   constant  
   case-label-list , constant  


proc-and-func-declaration:  
   proc-or-func  
   proc-and-func-declaration ; proc-or-func 


proc-or-func:  
   procedure  identifier parametersopt ;  block-or-forward 
   function  identifier parametersopt : typeid ; block-or-forward 

 
block-or-forward:  
   block  
   forward  


parameters:  
   ( formal-parameter-list )  


formal-parameter-list:  
   formal-parameter-section  
   formal-parameter-list ; formal-parameter-section  


formal-parameter-section:  
   parameterid-list : typeid 
   var parameterid-list : typeid  
   procedure identifier parametersopt 
   function identifier parametersopt : typeid 


parameterid-list:  
   identifier  
   parameterid-list , identifier  


statement-list:  
   statement  
   statement-list ; statement  


statement:  
   empty  
   variable := expression  
   begin statement-list end  
   if expression then statement 
   if expression then statement else statement  
   case expression of case-list end  
   while expression do statement  
   repeat statement-list until expression  
   for varid := for-list do statement  
   procid  
   procid ( expression-list )  
   goto label 
   with record-variable-list do statement  
   label : statement  


variable:  
   identifier  
   variable [ subscript-list ]  
   variable . fieldid  
   variable ^  


subscript-list:  
   expression  
   subscript-list , expression  


case-list:  
   case-label-list : statement  
   case-list ; case-label-list : statement  


for-list:  
   expression to expression  
   expression downto expression  


expression-list:  
   expression  
   expression-list , expression  


label:  
   unsigned-integer 


record-variable-list:  
   variable  
   record-variable-list , variable  


expression: 
   expression relational-op additive-expression 
   additive-expression  


relational-op: one of 
   <  <=  =  <>  =>  > 


additive-expression: 
   additive-expression additive-op multiplicative-expression 
   multiplicative-expression  


additive-op: one of 
   +  -  or 


multiplicative-expression: 
   multiplicative-expression multiplicative-op unary-expression 
   unary-expression  


multiplicative-op: one of 
   *  /  div  mod  and  in 


unary-expression: 
   unary-op unary-expression  
   primary-expression  


unary-op:  one of 
   +  -  not 


primary-expression:  
   variable  
   unsigned-integer  
   unsigned-real  
   string  
   nil  
   funcid ( expression-list )  
   [ element-list ]  
   ( expression )  


element-list:  
   empty  
   element  
   element-list , element  


element:  
   expression  
   expression ... expression  


constid:  
   identifier  


typeid:  
   identifier  


funcid: 
   identifier  


procid:  
   identifier  


fieldid:  
   identifier   

  
varid: 
   identifier  


empty: 

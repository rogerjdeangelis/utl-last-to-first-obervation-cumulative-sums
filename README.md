# utl-last-to-first-obervation-cumulative-sums
Last to first obervation cumulative sums 
    Last to first observation cumulative sums                                              
                                                                                           
    github                                                                                 
    https://tinyurl.com/yal94ku2                                                           
    https://github.com/rogerjdeangelis/utl-last-to-first-observation-cumulative-sums       
                                                                                           
    SAS Forum                                                                              
    https://communities.sas.com/t5/SAS-Programming/Conditional-sum/m-p/658933              
                                                                                           
    *_                   _                                                                 
    (_)_ __  _ __  _   _| |_                                                               
    | | '_ \| '_ \| | | | __|                                                              
    | | | | | |_) | |_| | |_                                                               
    |_|_| |_| .__/ \__,_|\__|                                                              
            |_|                                                                            
    ;                                                                                      
                                                                                           
    data have;                                                                             
    input VALUE;                                                                           
    cards4;                                                                                
    21                                                                                     
    22                                                                                     
    23                                                                                     
    24                                                                                     
    25                                                                                     
    ;;;;                                                                                   
    run;quit;                                                                              
                                                                                           
    *            _               _                                                         
      ___  _   _| |_ _ __  _   _| |_                                                       
     / _ \| | | | __| '_ \| | | | __|                                                      
    | (_) | |_| | |_| |_) | |_| | |_                                                       
     \___/ \__,_|\__| .__/ \__,_|\__|                                                      
                    |_|                                                                    
    ;                                                                                      
                                                                                           
    Up to 40 obs from WANT total obs=5                                                     
                                                                                           
                  | RULES                                                                  
                  | Reverse cumulative sums                                                
    Obs    VALUE  |                                                                        
                  |                                                                        
     1      115   | 25+24+23+22+21 = 115                                                   
     2       94   | 25+24+23+22    =  94                                                   
     3       72   | 25+24+23       =  72                                                   
     4       49   | ...                                                                    
     5       25   |                                                                        
                                                                                           
    *                                                                                      
     _ __  _ __ ___   ___ ___  ___ ___                                                     
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                    
    | |_) | | | (_) | (_|  __/\__ \__ \                                                    
    | .__/|_|  \___/ \___\___||___/___/                                                    
    |_|                                                                                    
    ;                                                                                      
                                                                                           
                                                                                           
    data want ;                                                                            
                                                                                           
      value = 0;                                                                           
                                                                                           
      set have(drop=value) curobs=cobs nobs=nobs;                                          
                                                                                           
      do pnt=cobs to nobs;                                                                 
          set have(rename=value=_value) point=pnt ;                                        
          value=sum(value, _value);                                                        
      end;                                                                                 
      output;                                                                              
                                                                                           
    run;quit;                                                                              
                                                                                           
                                                                                           
                                                                                           

# projetoDigme
Aplicação de troca de mensagens instantâneas

if($cpf){
                $urlCref= 'https://online.crefsc.org.br/spw/api_spw/cadastral/pessoafisica/cadastropersonalizado';               
                $header= array(
                    'Content-Type:application/json'
                );
                $data= ["chave"=> "",
                        "registro"=> "",
                        "cpf"=> $cpf,
                        ];

                $chInit= curl_init();
                

                curl_setopt($chInit, CURLOPT_URL, $url);
                curl_setopt($chInit, CURLOPT_POST, 1);
                curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
                curl_setopt($chInit, CURLOPT_POSTFIELDS, json_encode($data));

                $result = curl_exec($chInit);

                $result= json_encode($result, true);

                if($result->cpf != $cpf){
                    return array($this->inputname => get_string('cpf_invalid', 'profilefield_cpf'));
                }

                curl_close($chInit);                
            }

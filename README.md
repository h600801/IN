DEl 1:
endret på Frames og farge

    FRAMES=  40; % 2->
    colorP = 'red';         
DEl 2:
              
      addet to nye øyer i (function AddIslands)
        
        [x, y, z] = peaks(SURFACES);
        x = x * 3000 - 20000;
        y = y * 6000 + 8000;
        z = z * 1500 + 2000;
        s2 = surf(x, y, z, 'LineStyle', 'none', 'AmbientStrength', 0.7);
        s2.FaceColor = 'texturemap';
        s2.CData = textureForrest;

        [x, y] = meshgrid(-5000:5000);
        z = x .* 0;
        s3 = surf(x, y, z, 'LineStyle', 'none', 'AmbientStrength', 0.7);
        s3.FaceColor = 'texturemap';
        s3.CData = textureSea;

Del 3:

    lagde ny funksjon for å endre landskap
        function ChangeEnvironment(surfaceType)
            textureDesert = imread('desert.jpg');
            textureSea = imread('sea.jpg');
            textureForrest = imread('forrest.jpg');
            textureIce = imread('ice.jpg');
            
                switch surfaceType
                case 'ocean'
                   s1.CData = textureSea;
                    s2.CData = textureForrest;
                case 'island'
                    s1.CData = textureDesert;
                    s2.CData = textureForrest;
                case 'ice'
                    s1.CData = textureDesert;
                    s2.CData = textureIce;
            otherwise
                disp('Error');
            return;
            end

    maks hastighet 
       if vel > 1500
        vel = 1500;
        end
    end
Del 4:

        %% addet i  function ShowInfo() at hvis høyden er mindre enn 200, så kal det komme en alarm.
        if pos(3) < 200
        disp('ALARM: Height is less than 200!');
        end
        %% addet i  function Check kwh left () denne if setningen 
        if vel < 100
                    crash();
        
        %% endret i  function UpdateFuel() forbruks formelen slik at flyet bruker 5kwt for hver 100 enheter det stiger
         kwt = kwt - 0.003 - (vel/100) * 5;


   
    function UpdateFuel
        if (kwt < 0)
            EngineStop();
        else
            kwt = kwt - 0.003 - (vel/100) * 5;
                if vel < 100
                    crash();
                end
            end 
        end


    function ShowInfo()
        if (isvalid(fig)==false) 
            return;
        end

        if pos(3) < 200
        disp('ALARM: Height is less than 200!');
        end
        
        txtKwh.String = "KWh : " + int2str(kwt);  
        txt2.String = sprintf('Speed: %s  Height: %s', ...
            int2str(vel), int2str(pos(3)) );
        x = int2str(pos(1)); y = int2str(pos(2));
        txt1.String = sprintf('Coord: (X: %s, Y: %s)', x, y);
    end    
     

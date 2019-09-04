# d2rq-movie

**1. Load data to your mysql databse**

    ./data/kg_demo_movie.sql

**2. Open terminal**
    
    cd ./d2rq-0.8.1
    
**3. Create mapping.ttl**

    generate-mapping -o ./../movie_mapping.ttl -u root -p Philips@1 jdbc:mysql://localhost:3306/kg_demo_movie?useSSL=false&useUnicode=true&characterEncoding=utf8
    
    NOTE: if you want to support. please add:d2rq:jdbcDSN "jdbc:mysql://localhost/kg_demo_movie?useSSL=false&useUnicode=true&characterEncoding=utf8";
    
**4. Start D2R Server**       

    d2r-server ./../movie_mapping.ttl
    
**5. Test the Server**

    Open http://localhost:2020/ in a web browser. and click:this AJAX-based SPARQL Explorer.
    input SPARQL:
    SELECT DISTINCT ?s ?y ?m WHERE {
    ?s rdf:type:Person.
    ?s :personEnglishName "Andy Lau".
    ?s :personName  ?y.
    ?s :hasActedIn ?o.
     ?o :movieTitle ?m.
    }
    LIMIT 10
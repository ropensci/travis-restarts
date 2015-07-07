require 'travis'

def restart_travis(repo)
  p repo
  lb = Travis::Repository.find(ENV[repo]).last_build
  if !lb.nil?
    checkpr = lb.attributes['pull_request']
    lb_name = lb.branch_info
    if lb_name == 'master'
      lb.restart
      # p lb_name
    else
      if checkpr
        Travis::Repository.find(ENV[repo]).branches['master'].restart
        # p "other"
      else
        lb.restart
        Travis::Repository.find(ENV[repo]).branches['master'].restart
        # p "other"
      end
    end
  end
end

desc "Builds the ENV['TRAVIS_REPOSITORY'] travis job with token ENV['TRAVIS_TOKEN']"
task :runtravis do
  repos = ['TRAVIS_REPO_ALM','TRAVIS_REPO_ANTWEB','TRAVIS_REPO_ECOENGINE',
    'TRAVIS_REPO_ELASTIC','TRAVIS_REPO_GIT2R','TRAVIS_REPO_PALEOBIODB',
    'TRAVIS_REPO_RALTMETRIC','TRAVIS_REPO_RBHL','TRAVIS_REPO_RBISON','TRAVIS_REPO_REBIRD',
    'TRAVIS_REPO_RENTREZ','TRAVIS_REPO_RFIGSHARE','TRAVIS_REPO_RFISHBASE',
    'TRAVIS_REPO_RFISHERIES','TRAVIS_REPO_RGBIF','TRAVIS_REPO_RINAT',
    'TRAVIS_REPO_RNEXML','TRAVIS_REPO_RNOAA','TRAVIS_REPO_RPLOS','TRAVIS_REPO_RSNPS',
    'TRAVIS_REPO_RWBCLIMATE','TRAVIS_REPO_SOLR','TRAVIS_REPO_SPOCC','TRAVIS_REPO_TAXIZE',
    'TRAVIS_REPO_TESTDAT','TRAVIS_REPO_TREEBASE','TRAVIS_REPO_BOLD','TRAVIS_REPO_RNPN',
    'TRAVIS_REPO_PLOTLY','TRAVIS_REPO_RCROSSREF','TRAVIS_REPO_RGLOBI',
    'TRAVIS_REPO_RSELENIUM','TRAVIS_REPO_EML','TRAVIS_REPO_DVN','TRAVIS_REPO_RDATACITE',
    'TRAVIS_REPO_GEONAMES','TRAVIS_REPO_NEOTOMA',
    'TRAVIS_REPO_PRISM','TRAVIS_REPO_OTS','TRAVIS_REPO_FULLTEXT',
    'TRAVIS_REPO_GISTR','TRAVIS_REPO_GENDER','TRAVIS_REPO_RORCID','TRAVIS_REPO_BMC',
    'TRAVIS_REPO_ARXIV','TRAVIS_REPO_CKANR','TRAVIS_REPO_CLIFRO','TRAVIS_REPO_DASHBOARD',
    'TRAVIS_REPO_DEPENDENCIES','TRAVIS_REPO_FLORAS','TRAVIS_REPO_MUSEMETA',
    'TRAVIS_REPO_PANGAEAR','TRAVIS_REPO_PLEIADES','TRAVIS_REPO_RDPLA','TRAVIS_REPO_REOL',
    'TRAVIS_REPO_RERDDAP','TRAVIS_REPO_REUROPEANA','TRAVIS_REPO_RMETADATA',
    'TRAVIS_REPO_RNBN','TRAVIS_REPO_TAXIZESOAP','TRAVIS_REPO_TRAITS','TRAVIS_REPO_USABOUNDARIES',
    'TRAVIS_REPO_HATHI','TRAVIS_REPO_RIF','TRAVIS_REPO_RDOPA','TRAVIS_REPO_ETSEED',
    'TRAVIS_REPO_RVERTNET','TRAVIS_REPO_WELLKNOWN','TRAVIS_REPO_PARASITER','TRAVIS_REPO_FINCH',
    'TRAVIS_REPO_BINOMEN','TRAVIS_REPO_CHROMER','TRAVIS_REPO_IEEER',
    'TRAVIS_REPO_CSL','TRAVIS_REPO_ELASTICDSL','TRAVIS_REPO_GEOJSONIO','TRAVIS_REPO_LAWN',
    'TRAVIS_REPO_PROJ','TRAVIS_REPO_RCRYPTSY','TRAVIS_REPO_WEBCHEM','TRAVIS_REPO_JQR',
    'TRAVIS_REPO_INTERNETARCHIVE','TRAVIS_REPO_CARTOGRAPHER',
    'TRAVIS_REPO_ZENODO','TRAVIS_REPO_RRLITE','TRAVIS_REPO_REDISAPI','TRAVIS_REPO_OPENCONTEXT',
    'TRAVIS_REPO_ENIGMA','TRAVIS_REPO_RSUNLIGHT','TRAVIS_REPO_RTIMES',
    'TRAVIS_REPO_PYTAXIZE','TRAVIS_REPO_HTTSNAP','TRAVIS_REPO_ANALOGSEA',
    'TRAVIS_REPO_CANADIANA','TRAVIS_REPO_HTTPING','TRAVIS_REPO_COWSAY',
    'TRAVIS_REPO_DISCGOLF','TRAVIS_REPO_HTTPCODE','TRAVIS_REPO_FISHBASEAPI'
  ]

  Travis.access_token = ENV['TRAVIS_TOKEN']
  repos.each do |iter|
    restart_travis(iter)
  end
end

def restart_travis_local(repo)
  p repo
  lb = Travis::Repository.find(repo).last_build
  if !lb.nil?
    checkpr = lb.attributes['pull_request']
    lb_name = lb.branch_info
    if lb_name == 'master'
      lb.restart
    else
      if checkpr
        Travis::Repository.find(repo).branches['master'].restart
      else
        lb.restart
        Travis::Repository.find(repo).branches['master'].restart
      end
    end
  end
end

desc "Builds a travis job for a Github repo of the form <owner/repo> with token ENV['TRAVIS_TOKEN']"
task :restart do
  var = ENV['var']
  Travis.access_token = ENV['TRAVIS_TOKEN']
  puts var
  puts "Restarting build for: #{var}"
  restart_travis_local(var)
end

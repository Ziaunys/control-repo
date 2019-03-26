def cd4pe(cd4pe_instance, domain, peName, moduleName, default = :control_branch)
  require 'net/http'; require 'json'
  begin
    environment = @librarian.environment.name
    uri = URI("#{cd4pe_instance}/get-pe-module-version")
    params = { op:'GetPEModuleVersion', domain:domain, peName:peName, moduleName:moduleName, environment:environment }
    uri.query = URI.encode_www_form(params)
    res = Net::HTTP.get_response(uri)
    res.is_a?(Net::HTTPSuccess) ? JSON.parse(res.body) : default
  rescue
    default
  end
end



forge 'https://forge.puppet.com'

# Modules from the Puppet Forge
# Versions should be updated to be the latest at the time you start
#mod 'puppetlabs/inifile',     '2.2.1'
mod 'puppetlabs/stdlib',      '4.25.1'
mod 'puppetlabs/concat',      '4.2.1'
mod 'puppetlabs-puppet_authorization', '0.5.0'

# Modules from Git
# Examples: https://github.com/puppetlabs/r10k/blob/master/doc/puppetfile.mkd#examples
#mod 'apache',
#  :git    => 'https://github.com/puppetlabs/puppetlabs-apache',
#  :commit => 'de290646f97e04b4b8e42c70f6e01e860c394ce7'

#mod 'apache',
#  :git    => 'https://github.com/puppetlabs/puppetlabs-apache',
#  :branch => 'docs_experiment'
:ref => cd4pe('http://localhost:8050', 'd3', 'test-pe3', 'puppetlabs-concat')

mod 'puppetlabs-cd4pe', :latest
mod 'puppetlabs-hocon', '1.0.1'
mod 'puppetlabs-docker', '3.2.0'
mod 'puppetlabs-apt', '6.2.1'
mod 'puppetlabs-translate', '1.1.0'

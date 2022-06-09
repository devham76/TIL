

@Configuration
@EnableWebMvc
class WebMvcConfigure : WebMvcConfigurer {

    override fun configureMessageConverters(converters: MutableList<HttpMessageConverter<*>>) {
        converters.add(MappingJackson2HttpMessageConverter())
        converters.add(StringHttpMessageConverter()) // default
    }


The Default Message Converters
By default, the following HttpMessageConverters instances are pre-enabled:

ByteArrayHttpMessageConverter – converts byte arrays
StringHttpMessageConverter – converts Strings
ResourceHttpMessageConverter – converts org.springframework.core.io.Resource for any type of octet stream
SourceHttpMessageConverter – converts javax.xml.transform.Source
FormHttpMessageConverter – converts form data to/from a MultiValueMap<String, String>.
Jaxb2RootElementHttpMessageConverter – converts Java objects to/from XML (added only if JAXB2 is present on the classpath)
MappingJackson2HttpMessageConverter – converts JSON (added only if Jackson 2 is present on the classpath)
MappingJacksonHttpMessageConverter – converts JSON (added only if Jackson is present on the classpath)
AtomFeedHttpMessageConverter – converts Atom feeds (added only if Rome is present on the classpath)
RssChannelHttpMessageConverter – converts RSS feeds (added only if Rome is present on the classpath)



https://www.baeldung.com/spring-httpmessageconverter-rest
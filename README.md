@GetMapping(value = "/get-image-with-media-type", produces = MediaType.IMAGE_JPEG_VALUE)
    public @ResponseBody byte[] getImageWithMediaType() throws IOException {
        final InputStream in = getClass().getResourceAsStream("/com/baeldung/produceimage/image.jpg");
        return IOUtils.toByteArray(in);
    }

    @GetMapping(value = "/get-file", produces = MediaType.APPLICATION_OCTET_STREAM_VALUE)
    public @ResponseBody byte[] getFile() throws IOException {
        final InputStream in = getClass().getResourceAsStream("/com/baeldung/produceimage/data.txt");
        return IOUtils.toByteArray(in);
    }
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.stream.Stream;

 try(Stream<String> lines = 
        Files.lines(Paths.get("tempest.txt"))){       
      
      lines.forEach(line -> 
        System.out.println("Line: " + line));

    
    Path file = Paths.get("tempest.txt");
    List<String> fileArr;
        
    try{       
            
      fileArr = Files.readAllLines(file);
            
      fileArr.stream()
        .filter(line -> line.contains("PROSPERO"))
        .forEach(line -> System.out.println(line));

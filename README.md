public class keywordidentifier {
    public static void main(String[] args) {
        // Java keywords list
        String[] keywords = {
                "abstract", "assert", "boolean", "break", "byte", "case", "catch", "char", "class", "const",
                "continue", "default", "do", "double", "else", "enum", "extends", "final", "finally",
                "float", "for", "goto", "if", "implements", "import", "instanceof", "int", "interface",
                "long", "native", "new", "package", "private", "protected", "public", "return", "short",
                "static", "strictfp", "super", "switch", "synchronized", "this", "throw", "throws",
                "transient", "try", "void", "volatile", "while"
        };

        // Combine keywords into a regex pattern
        StringBuilder keywordPatternBuilder = new StringBuilder();
        for (int i = 0; i < keywords.length; i++) {
            keywordPatternBuilder.append("\\b").append(keywords[i]).append("\\b");
            if (i < keywords.length - 1) {
                keywordPatternBuilder.append("|");
            }
        }

        String keywordPattern = keywordPatternBuilder.toString();

        // Sample input
        String input = "public class Test { public static void main(String[] args) { int x = 10; if (x > 5) { System.out.println(\"x is greater than 5\"); } } }";

        // Compile and match the pattern
        Pattern pattern = Pattern.compile(keywordPattern);
        Matcher matcher = pattern.matcher(input);

        System.out.println("Identified Java Keywords:");
        while (matcher.find()) {
            System.out.println(matcher.group());
        }
    }
}

import java.util.Scanner; 
import java.util.Random;
import java.util.HashMap;
import java.util.Map;

public class JogoDePalavras {
    private static Map<String, String[]> categoriasPalavras = new HashMap<>();
    
    static {
        categoriasPalavras.put("Animais", new String[]{"cachorro", "gato", "elefante", "leão", "tigre", "macaco"});
        categoriasPalavras.put("Frutas", new String[]{"banana", "laranja", "maçã", "uva", "morango", "abacaxi"});
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Escolha uma categoria:");
        for (String categoria : categoriasPalavras.keySet()) {
            System.out.println("- " + categoria);
        }
        System.out.print("Categoria: ");
        String categoriaEscolhida = scanner.nextLine();

        String palavra = selecionarPalavraAleatoria(categoriaEscolhida);
        
        char[] letrasAdivinhadas = new char[palavra.length()];
        for (int i = 0; i < letrasAdivinhadas.length; i++) {
            letrasAdivinhadas[i] = '_';
        }

        int maxTentativas = 6;
        int tentativas = 0;

        // Loop principal do jogo
        
        while (tentativas < maxTentativas) {

            System.out.println("Palavra: " + String.valueOf(letrasAdivinhadas));

            
            System.out.print("Digite uma letra: ");
            char letra = scanner.next().charAt(0);

            
            if (jaFoiTentada(letra, letrasAdivinhadas)) {
                System.out.println("Você já tentou essa letra antes. Tente novamente.");
                continue;
            }

            boolean letraEncontrada = false;
            for (int i = 0; i < palavra.length(); i++) {
                if (palavra.charAt(i) == letra) {
                    letrasAdivinhadas[i] = letra;
                    letraEncontrada = true;
                }
            }

            if (String.valueOf(letrasAdivinhadas).equals(palavra)) {
                System.out.println("Parabéns! Você adivinhou a palavra correta: " + palavra);
                break;
            }

            
            if (!letraEncontrada) {
                tentativas++;
                System.out.println("Letra não encontrada. Tentativas restantes: " + (maxTentativas - tentativas));
            }
        }

        
        if (tentativas == maxTentativas) {
            System.out.println("Você excedeu o número máximo de tentativas. A palavra correta era: " + palavra);
        }
        scanner.close();
    }

    private static String selecionarPalavraAleatoria(String categoria) {
        Random random = new Random();
        String[] palavrasCategoria = categoriasPalavras.get(categoria);
        return palavrasCategoria[random.nextInt(palavrasCategoria.length)];
    }

    private static boolean jaFoiTentada(char letra, char[] letrasAdivinhadas) {
        for (char c : letrasAdivinhadas) {
            if (c == letra) {
                return true;
            }
        }
        return false;
    }
}

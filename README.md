# EstudosJavaBB


<br>


# Jogo de adivinhacao


<br>


import java.util.Random;
import java.util.Scanner;

public class JogoAdivinhacao {

    public static void main(String[] args) {

        Scanner resposta = new Scanner(System.in);
        Scanner tentativaAdivinha = new Scanner(System.in);
        String continua = "";
        String pensando = "\"pensando\"";
        String novamente = "novamente ?";
        String fraseFinalGame = "";
        int mediaFinalTentativasPartidas;
        int numeroPensado;
        int numeroAdivinha;
        int contador = 0;
        int contadorTentativas = 0;
        int totalTentativasJogoTodasPartidas = 0;
        int contadorPartidas = 0;

        while (!continua.equals("n")){
            numeroPensado = new Random().nextInt(100);
            System.out.println(numeroPensado);
            numeroAdivinha = 101;

            if(contador < 1){
                System.out.println("Bem vindo ao jogo de adivinhacão!");
                contador = 1;
            }
            if(contador > 1){
                System.out.println("Gostaria de jogar " + novamente + " S (sim) | N (não)");
                continua = resposta.nextLine().toLowerCase();
            }
            if(contador == 1 ){
                System.out.println("Gostaria de jogar? S (sim) | N (não)");
                continua = resposta.nextLine().toLowerCase();
                contador++;
            }
            if(continua.equals("s")) {
                contadorTentativas = 0;
                System.out.println("Certo, vamos começar!");
                System.out.println("Tente adivinhar o número que eu estou " + pensando);
                System.out.println("É um número inteiro entre 0 e 100!");
                while(numeroAdivinha != numeroPensado){
                    System.out.println("Digite o número abaixo:");
                    numeroAdivinha = tentativaAdivinha.nextInt();
                    contadorTentativas ++;
                    totalTentativasJogoTodasPartidas ++;
                    if(numeroAdivinha == numeroPensado){
                        contadorPartidas++;
                        if(contadorTentativas == 1){
                            System.out.println("Uau! Você é realmente incrível, acertou com apenas uma tentativa!!!");
                            break;
                        }else{
                            System.out.println("Parabéns, você acertou com um total de "+ contadorTentativas +" tentativas!");
                            System.out.println("O número que eu pensei foi o "+ numeroPensado);
                            break;
                        }
                    } else if (numeroAdivinha > numeroPensado) {
                        System.out.println("Ainda não, tente um número MENOR.");
                    } else if (numeroAdivinha < numeroPensado) {
                        System.out.println("Ainda não, tente um número MAIOR.");
                    } else {
                        System.out.println("Resposta inválida, tente novamente!");
                    }
                }
            }else if(continua.equals("n")){
                if (contador >= 2){
                    mediaFinalTentativasPartidas = totalTentativasJogoTodasPartidas/contadorPartidas;
                    if(mediaFinalTentativasPartidas>=8) {
                        fraseFinalGame = "Vish!! Pode melhorar... Continue praticando, seu resultado foi bem abaixo do esperado...";
                    }else if(mediaFinalTentativasPartidas == 1) {
                        fraseFinalGame = " Wooooooooooow!!!!!! SUA MÉDIA É " + mediaFinalTentativasPartidas + "?!!!! Absolutamente incrível, você com certeza não é humano! (ou é um programador rsrsrs)";
                    }else if(mediaFinalTentativasPartidas<=5){
                        fraseFinalGame = " Parabéns, você é muito bom nesse jogo! Resultado além do esperado!";
                    }else {
                        fraseFinalGame = " Parabéns, seu resultado está dentro do esperado.";

                    }
                    System.out.println("Muito obrigado por jogar!");
                    System.out.println("Você jogou " + contadorPartidas + " partidas, com um total de " + totalTentativasJogoTodasPartidas + " tentativas!");
                    System.out.println("A sua média é de " + mediaFinalTentativasPartidas + " tentativas por partida." + fraseFinalGame);
                    break;

                }
                System.out.println("Certo, até breve!");
                break;
            }else{
                System.out.println("Resposta inválida! Tente novamente.");
            }
        }
    }
}

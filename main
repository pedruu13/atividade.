from abc import ABC, abstractmethod


class CanalComunicacao(ABC):
    def __init__(self, identificador):
        self.identificador = identificador

    @abstractmethod
    def enviar_mensagem(self, mensagem):
        pass


class MensagemTexto:
    def __init__(self, mensagem, data_envio):
        self.mensagem = mensagem
        self.data_envio = data_envio

class MensagemVideo:
    def __init__(self, mensagem, arquivo, formato, duracao):
        self.mensagem = mensagem
        self.arquivo = arquivo
        self.formato = formato
        self.duracao = duracao

class MensagemFoto:
    def __init__(self, mensagem, arquivo, formato):
        self.mensagem = mensagem
        self.arquivo = arquivo
        self.formato = formato

class MensagemArquivo:
    def __init__(self, mensagem, arquivo, formato):
        self.mensagem = mensagem
        self.arquivo = arquivo
        self.formato = formato


class WhatsApp(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem via WhatsApp para {self.identificador}: {mensagem.mensagem}, Data: {mensagem.data_envio}")

class Telegram(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem via Telegram para {self.identificador}: {mensagem.mensagem}")

class Facebook(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem via Facebook para {self.identificador}: {mensagem.mensagem}")

class Instagram(CanalComunicacao):
    def enviar_mensagem(self, mensagem):
        print(f"Enviando mensagem via Instagram para {self.identificador}: {mensagem.mensagem}")


class AplicacaoChatbot:
    def __init__(self):
        self.canais = {}

    def adicionar_canal(self, nome_canal, canal):
        self.canais[nome_canal] = canal

    def enviar_mensagem_para_canal(self, nome_canal, tipo_mensagem, *args, **kwargs):
        canal = self.canais.get(nome_canal)
        if canal:
            mensagem = tipo_mensagem(*args, **kwargs)
            canal.enviar_mensagem(mensagem)
        else:
            print(f"Canal {nome_canal} não encontrado.")


if __name__ == "__main__":
    aplicacao = AplicacaoChatbot()

  
    aplicacao.adicionar_canal("whatsapp", WhatsApp("123456789"))
    aplicacao.adicionar_canal("telegram", Telegram("@usuario_telegram"))
    aplicacao.adicionar_canal("facebook", Facebook("usuario_facebook"))
    aplicacao.adicionar_canal("instagram", Instagram("usuario_instagram"))

  
    mensagem_whatsapp = MensagemTexto("Olá, mundo!", "01/01/2023")
    mensagem_telegram = MensagemVideo("Vídeo legal", "video.mp4", "mp4", "5 minutos")
    mensagem_facebook = MensagemFoto("Linda paisagem", "foto.jpg", "jpg")
    mensagem_instagram = MensagemArquivo("Documento importante", "documento.pdf", "pdf")

   
    aplicacao.enviar_mensagem_para_canal("whatsapp", MensagemTexto, "Olá, mundo!", "01/01/2023")
    aplicacao.enviar_mensagem_para_canal("telegram", MensagemVideo, "Vídeo legal", "video.mp4", "mp4", "5 minutos")
    aplicacao.enviar_mensagem_para_canal("facebook", MensagemFoto, "Linda paisagem", "foto.jpg", "jpg")
    aplicacao.enviar_mensagem_para_canal("instagram", MensagemArquivo, "Documento importante", "documento.pdf", "pdf")

# TTSs

Coqui XTTS ile metni sese çeviren bir komut satırı betiği. Metin cümlelere bölünür, her cümle bir referans konuşmacı kaydına koşullu olarak sentezlenir ve parçalar tek bir WAV dosyasında birleştirilir.

Betik `ttts/tts.py` içindedir. Çalıştırmadan önce `main()` içindeki şu yolları kendi makinenize göre değiştirin:

- XTTS checkpoint (`best_model.pth`)
- model config ve vocab JSON dosyaları
- referans konuşmacı WAV dosyası
- çıktı klasörü

## Kurulum

```bash
pip install TTS torch torchaudio
```

CUDA varsa model GPU'ya alınır. Yoksa CPU'da yüklenir.

## Çalıştırma

`ttts/tts.py` şu haliyle başlamaz: `combined_wav` satırı girintisiz ve giriş kontrolü `if name == "main"` yazılmış. Bunlar düzeltilmeden betik çalışmaz.

```bash
python ttts/tts.py
```

Metni satır satır yapıştırın ve boş bir satırla gönderin. Şiir satırlarının sonuna, cümle sonu yoksa virgül eklenir; sonra metin `.`, `!` ve `?` işaretlerinden bölünür. Her turda `genclige_hitabeN.wav` adıyla yeni bir dosya yazılır. Çıkmak için boş metin gönderin veya `Ctrl+D` kullanın.

Sentez dili kodda `en` olarak sabittir. Türkçe çıktı için `run_tts` içindeki `language` değerini değiştirmeniz gerekir.

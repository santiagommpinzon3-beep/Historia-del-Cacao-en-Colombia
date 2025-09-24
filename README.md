import qrcode
from PIL import Image, ImageOps

# URL local sugerida (el usuario puede cambiarla si sube el archivo a un hosting)
# Por ahora usaré un enlace genérico como ejemplo (puede ser una ruta en GitHub Pages o similar).
# Si el usuario no tiene hosting, el QR solo funcionará una vez que suba la página a Internet.
# Para que pueda probarlo de inmediato, haré un QR que apunte a un texto corto con instrucciones.
qr_text = "Instrucciones: este QR apunta a tu archivo index.html. " \
          "Para que funcione, sube tu página a un hosting (GitHub Pages, Netlify, etc.) " \
          "y luego reemplaza este texto por la URL final."

out_path_qr = "/mnt/data/pagina_cacao_qr.png"

# Generar el código QR con buena resolución y borde
qr = qrcode.QRCode(error_correction=qrcode.constants.ERROR_CORRECT_H, box_size=12, border=4)
qr.add_data(qr_text)
qr.make(fit=True)
img_qr = qr.make_image(fill_color="black", back_color="white").convert("RGB")
img_qr = ImageOps.expand(img_qr, border=8, fill='white')
img_qr.save(out_path_qr)

out_path_qr

#!/bin/bash

# Directorio de entrada (donde se encuentran los archivos PNG originales)
input_dir="."
# Directorio de salida (donde se guardarán los archivos WebP y escalados)
output_dir="."

# Crear el directorio de salida si no existe
mkdir -p "$output_dir"

# Recorre todos los archivos PNG en el directorio de entrada
for png_file in "$input_dir"/*.png; do
    # Nombre base del archivo sin la extensión
    base_name=$(basename "$png_file" .png)

    # Convertir PNG a WebP
    ffmpeg -i "$png_file" -c:v webp "$output_dir/$base_name.webp"

    # Escalar el archivo WebP a 20x20 píxeles
    ffmpeg -i "$output_dir/$base_name.webp" -vf "scale=20:20" "$output_dir/${base_name}-resized.webp"
done

echo "La conversión y el escalado han finalizado."

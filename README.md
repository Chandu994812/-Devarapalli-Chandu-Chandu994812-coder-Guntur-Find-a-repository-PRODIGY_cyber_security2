# -Devarapalli-Chandu-Chandu994812-coder-Guntur-Find-a-repository-PRODIGY_cyber_security2
prodigy 2nd task





from PIL import Image

def encrypt_image(input_image, output_image, key):
    """
    Encrypts an image using pixel manipulation.

    Args:
        input_image (str): The path to the input image file.
        output_image (str): The path to the output encrypted image file.
        key (int): The encryption key (a constant value to be added/subtracted).
    """
    # Load the input image
    image = Image.open(input_image)
    width, height = image.size

    # Iterate through the pixels and perform encryption
    encrypted_pixels = []
    for y in range(height):
        for x in range(width):
            r, g, b = image.getpixel((x, y))
            # Perform pixel manipulation (e.g., add the key to each RGB value)
            encrypted_r = (r + key) % 256
            encrypted_g = (g + key) % 256
            encrypted_b = (b + key) % 256
            encrypted_pixels.append((encrypted_r, encrypted_g, encrypted_b))

    # Create the encrypted image and save it
    encrypted_image = Image.new(image.mode, image.size)
    encrypted_image.putdata(encrypted_pixels)
    encrypted_image.save(output_image)

def decrypt_image(input_image, output_image, key):
    """
    Decrypts an encrypted image using pixel manipulation.

    Args:
        input_image (str): The path to the input encrypted image file.
        output_image (str): The path to the output decrypted image file.
        key (int): The decryption key (the same value used for encryption).
    """
    # Load the encrypted image
    image = Image.open(input_image)
    width, height = image.size

    # Iterate through the pixels and perform decryption
    decrypted_pixels = []
    for y in range(height):
        for x in range(width):
            r, g, b = image.getpixel((x, y))
            # Perform the inverse pixel manipulation (e.g., subtract the key from each RGB value)
            decrypted_r = (r - key) % 256
            decrypted_g = (g - key) % 256
            decrypted_b = (b - key) % 256
            decrypted_pixels.append((decrypted_r, decrypted_g, decrypted_b))

    # Create the decrypted image and save it
    decrypted_image = Image.new(image.mode, image.size)
    decrypted_image.putdata(decrypted_pixels)
    decrypted_image.save(output_image)

# Example usage
encrypt_image('input_image.jpg', 'encrypted_image.jpg', key=42)
decrypt_image('encrypted_image.jpg', 'decrypted_image.jpg', key=42)

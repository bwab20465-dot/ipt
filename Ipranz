#!/usr/bin/env python3
# -*- coding: utf-8 -*-
# RANZ WORMV2 - Termux Tool
# Author: Raiz
# Telegram: t.me/Ranzkecebet

import os
import sys
import socket
import requests
import json
from urllib.parse import urlparse
import time

# Class untuk warna terminal
class Colors:
    # Warna dasar
    RED = '\033[31m'
    GREEN = '\033[32m'
    YELLOW = '\033[33m'
    BLUE = '\033[34m'
    MAGENTA = '\033[35m'
    CYAN = '\033[36m'
    WHITE = '\033[37m'
    BLACK = '\033[30m'
    
    # Background colors
    BG_RED = '\033[41m'
    BG_GREEN = '\033[42m'
    BG_YELLOW = '\033[43m'
    BG_BLUE = '\033[44m'
    BG_MAGENTA = '\033[45m'
    BG_CYAN = '\033[46m'
    BG_WHITE = '\033[47m'
    BG_BLACK = '\033[40m'
    
    # Styles
    BOLD = '\033[1m'
    UNDERLINE = '\033[4m'
    BLINK = '\033[5m'
    REVERSE = '\033[7m'
    
    # Reset
    RESET = '\033[0m'

def clear_screen():
    """Membersihkan layar terminal"""
    os.system('clear' if os.name == 'posix' else 'cls')

def display_banner():
    """Menampilkan banner dengan animasi"""
    banner = f"""{Colors.GREEN}
╔══════════════════════════════════════════╗
║                                          ║
║    {Colors.BOLD}{Colors.WHITE}[ RANZ WORMV2 active ]{Colors.RESET}{Colors.GREEN}          ║
║                                          ║
║    {Colors.WHITE}Advanced IP Lookup Tool{Colors.GREEN}             ║
║    {Colors.WHITE}For Termux Terminal{Colors.GREEN}                 ║
║                                          ║
╚══════════════════════════════════════════╝{Colors.RESET}
"""
    print(banner)

def display_menu():
    """Menampilkan menu utama"""
    menu_items = [
        "1. 📱 Developer Info",
        "2. 🔍 Search IP Location",
        "3. 🌐 Check Multiple Websites",
        "4. 📊 My Network Info",
        "5. 🧹 Clear Screen",
        "6. 🚪 Exit"
    ]
    
    print(f"\n{Colors.CYAN}{Colors.BOLD}╔{'═'*35}╗")
    print(f"║{' '*9}MAIN MENU{' '*10}║")
    print(f"╚{'═'*35}╝{Colors.RESET}\n")
    
    for item in menu_items:
        color = Colors.YELLOW if "1" in item else \
                Colors.GREEN if "2" in item else \
                Colors.BLUE if "3" in item else \
                Colors.MAGENTA if "4" in item else \
                Colors.CYAN if "5" in item else \
                Colors.RED
        print(f"  {color}{item}{Colors.RESET}")
    
    print(f"\n{Colors.WHITE}{'─'*50}{Colors.RESET}")

def rainbow_box(text_lines):
    """Membuat kotak dengan warna pelangi"""
    colors = [Colors.BG_RED, Colors.BG_YELLOW, Colors.BG_GREEN, 
              Colors.BG_CYAN, Colors.BG_BLUE, Colors.BG_MAGENTA]
    
    max_len = max(len(line) for line in text_lines) + 8
    
    # Top border dengan warna pelangi
    top_border = ""
    for i in range(max_len + 2):
        color = colors[i % len(colors)]
        top_border += f"{color} {Colors.RESET}"
    
    print(f"\n{Colors.BOLD}{top_border}{Colors.RESET}")
    
    # Konten dengan border warna-warni
    for idx, line in enumerate(text_lines):
        color_idx = idx % len(colors)
        border_color = colors[color_idx]
        spaces = max_len - len(line) - 4
        
        print(f"{border_color} {Colors.RESET}  {Colors.BOLD}{Colors.WHITE}{line}{' '*spaces}  {border_color} {Colors.RESET}")
    
    # Bottom border
    bottom_border = ""
    for i in range(max_len + 2):
        color = colors[(i + 3) % len(colors)]
        bottom_border += f"{color} {Colors.RESET}"
    
    print(f"{Colors.BOLD}{bottom_border}{Colors.RESET}\n")

def show_developer_info():
    """Menampilkan informasi developer dengan kotak warna-warni"""
    info_lines = [
        "╔══════════════════════════╗",
        "║     DEVELOPER INFO       ║",
        "╠══════════════════════════╣",
        "║                          ║",
        "║  📱 telegram: t.me/Ranzkecebet",
        "║  👤 author: Raiz         ║",
        "║  🛠️  version: WORMV2.0    ║",
        "║  🐍 language: Python     ║",
        "║  📅 created: 2024        ║",
        "║                          ║",
        "╚══════════════════════════╝"
    ]
    
    rainbow_box(info_lines)
    
    # Animasi teks tambahan
    print(f"{Colors.BOLD}{Colors.CYAN}Additional Information:{Colors.RESET}")
    print(f"{Colors.WHITE}┌{'─'*48}┐")
    print(f"│ {Colors.YELLOW}📍 This tool is for educational purposes only{Colors.WHITE}  │")
    print(f"│ {Colors.GREEN}📍 Always use tools responsibly{Colors.WHITE}               │")
    print(f"│ {Colors.BLUE}📍 Respect privacy and network security{Colors.WHITE}        │")
    print(f"└{'─'*48}┘{Colors.RESET}")

def extract_domain(url):
    """Ekstrak domain dari URL"""
    try:
        if not url.startswith(('http://', 'https://')):
            url = 'https://' + url
        
        parsed = urlparse(url)
        domain = parsed.netloc
        
        if domain.startswith('www.'):
            domain = domain[4:]
        
        return domain
    except:
        return None

def get_ip_from_domain(domain):
    """Mendapatkan IP address dari domain"""
    try:
        return socket.gethostbyname(domain)
    except:
        return None

def get_ip_info(ip_address):
    """Mendapatkan informasi lokasi dari IP"""
    try:
        response = requests.get(f"http://ip-api.com/json/{ip_address}", timeout=10)
        data = response.json()
        
        if data['status'] == 'success':
            return {
                'country': data['country'],
                'region': data['regionName'],
                'city': data['city'],
                'isp': data['isp'],
                'lat': data['lat'],
                'lon': data['lon'],
                'timezone': data['timezone'],
                'org': data['org']
            }
        return None
    except:
        return None

def search_ip_location():
    """Fungsi untuk mencari lokasi IP"""
    print(f"\n{Colors.BOLD}{Colors.CYAN}╔{'═'*45}╗")
    print(f"║{' '*8}SEARCH IP LOCATION{' '*8}║")
    print(f"╚{'═'*45}╝{Colors.RESET}\n")
    
    print(f"{Colors.YELLOW}📝 Contoh input:{Colors.RESET}")
    print(f"  {Colors.WHITE}• https://www.google.com{Colors.RESET}")
    print(f"  {Colors.WHITE}• google.com{Colors.RESET}")
    print(f"  {Colors.WHITE}• 8.8.8.8 (IP langsung){Colors.RESET}")
    print(f"\n{Colors.WHITE}{'─'*50}{Colors.RESET}")
    
    while True:
        target = input(f"\n{Colors.GREEN}🎯 Masukkan URL/IP (atau 'back' untuk kembali): {Colors.RESET}").strip()
        
        if target.lower() == 'back':
            return
        
        if not target:
            print(f"{Colors.RED}❌ Input tidak boleh kosong!{Colors.RESET}")
            continue
        
        print(f"\n{Colors.BLUE}⏳ Memproses...{Colors.RESET}")
        
        # Cek apakah input adalah IP address
        is_ip = False
        try:
            socket.inet_aton(target)
            is_ip = True
            ip_address = target
            domain = None
        except:
            is_ip = False
        
        if not is_ip:
            # Input adalah URL/domain
            domain = extract_domain(target)
            if not domain:
                print(f"{Colors.RED}❌ Format URL tidak valid!{Colors.RESET}")
                continue
            
            print(f"{Colors.GREEN}✅ Domain terdeteksi: {domain}{Colors.RESET}")
            
            # Cari IP dari domain
            print(f"{Colors.BLUE}🔍 Mencari IP address...{Colors.RESET}")
            ip_address = get_ip_from_domain(domain)
            
            if not ip_address:
                print(f"{Colors.RED}❌ Gagal mendapatkan IP dari domain!{Colors.RESET}")
                continue
            
            print(f"{Colors.GREEN}✅ IP Address ditemukan: {ip_address}{Colors.RESET}")
        else:
            domain = ip_address
        
        # Dapatkan informasi lokasi
        print(f"{Colors.BLUE}🌍 Mencari informasi lokasi...{Colors.RESET}")
        location_info = get_ip_info(ip_address)
        
        # Tampilkan hasil
        print(f"\n{Colors.BOLD}{Colors.GREEN}╔{'═'*45}╗")
        print(f"║{' '*10}HASIL PENCARIAN{' '*10}║")
        print(f"╚{'═'*45}╝{Colors.RESET}\n")
        
        if location_info:
            result_box = [
                f"🌐 Target: {target}",
                f"📡 IP Address: {ip_address}",
                f"🏳️  Negara: {location_info['country']}",
                f"📍 Region: {location_info['region']}",
                f"🏙️  Kota: {location_info['city']}",
                f"⚡ ISP: {location_info['isp']}",
                f"🏢 Organisasi: {location_info['org']}",
                f"🕐 Timezone: {location_info['timezone']}",
                f"🗺️  Koordinat: {location_info['lat']}, {location_info['lon']}"
            ]
            
            rainbow_box(result_box)
        else:
            print(f"{Colors.YELLOW}⚠️  Informasi lokasi tidak ditemukan, hanya IP:{Colors.RESET}")
            print(f"{Colors.CYAN}┌{'─'*30}┐")
            print(f"│ 📡 IP Address: {ip_address:15} │")
            if domain != ip_address:
                print(f"│ 🌐 Domain: {domain:20} │")
            print(f"└{'─'*30}┘{Colors.RESET}")
        
        # Tanya apakah ingin mencari lagi
        print(f"\n{Colors.WHITE}{'─'*50}{Colors.RESET}")
        again = input(f"\n{Colors.YELLOW}🔁 Cari lagi? (y/n): {Colors.RESET}").lower()
        if again != 'y':
            break

def check_network_info():
    """Menampilkan informasi jaringan lokal"""
    try:
        hostname = socket.gethostname()
        local_ip = socket.gethostbyname(hostname)
        
        print(f"\n{Colors.BOLD}{Colors.MAGENTA}╔{'═'*45}╗")
        print(f"║{' '*8}NETWORK INFORMATION{' '*8}║")
        print(f"╚{'═'*45}╝{Colors.RESET}\n")
        
        info_lines = [
            f"🖥️  Hostname: {hostname}",
            f"📶 Local IP: {local_ip}",
            f"🌐 Public IP: Getting info...",
            f"🔧 System: {sys.platform}"
        ]
        
        rainbow_box(info_lines)
        
        # Coba dapatkan public IP
        try:
            public_ip = requests.get('https://api.ipify.org', timeout=5).text
            print(f"{Colors.GREEN}✅ Public IP: {public_ip}{Colors.RESET}")
            
            # Dapatkan info lokasi dari public IP
            public_info = get_ip_info(public_ip)
            if public_info:
                print(f"\n{Colors.CYAN}📍 Lokasi Public IP:{Colors.RESET}")
                print(f"   {Colors.WHITE}• Negara: {public_info['country']}")
                print(f"   {Colors.WHITE}• Kota: {public_info['city']}")
                print(f"   {Colors.WHITE}• ISP: {public_info['isp']}{Colors.RESET}")
        except:
            print(f"{Colors.YELLOW}⚠️  Tidak dapat mendapatkan public IP{Colors.RESET}")
            
    except Exception as e:
        print(f"{Colors.RED}❌ Error: {str(e)}{Colors.RESET}")

def main():
    """Fungsi utama"""
    # Cek dependencies
    try:
        import requests
    except ImportError:
        print(f"{Colors.RED}❌ Package 'requests' belum terinstall!{Colors.RESET}")
        print(f"{Colors.YELLOW}📦 Install dengan: pip install requests{Colors.RESET}")
        return
    
    clear_screen()
    display_banner()
    
    while True:
        display_menu()
        
        try:
            choice = input(f"\n{Colors.BOLD}{Colors.GREEN}👉 Pilih menu [1-6]: {Colors.RESET}").strip()
            
            if choice == '1':
                show_developer_info()
            elif choice == '2':
                search_ip_location()
            elif choice == '3':
                print(f"\n{Colors.YELLOW}⚠️  Fitur ini dalam pengembangan...{Colors.RESET}")
            elif choice == '4':
                check_network_info()
            elif choice == '5':
                clear_screen()
                display_banner()
                continue
            elif choice == '6':
                print(f"\n{Colors.GREEN}👋 Terima kasih telah menggunakan RANZ WORMV2{Colors.RESET}")
                print(f"{Colors.CYAN}📱 Telegram: t.me/Ranzkecebet{Colors.RESET}")
                print(f"{Colors.YELLOW}✨ Goodbye!{Colors.RESET}\n")
                sys.exit(0)
            else:
                print(f"{Colors.RED}❌ Pilihan tidak valid! Silakan pilih 1-6{Colors.RESET}")
            
            input(f"\n{Colors.WHITE}⏎ Tekan Enter untuk melanjutkan...{Colors.RESET}")
            clear_screen()
            display_banner()
            
        except KeyboardInterrupt:
            print(f"\n\n{Colors.RED}❌ Program dihentikan{Colors.RESET}")
            sys.exit(0)
        except Exception as e:
            print(f"\n{Colors.RED}💥 Error: {str(e)}{Colors.RESET}")

if __name__ == "__main__":
    main()

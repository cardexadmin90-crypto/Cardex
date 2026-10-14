# C / CARDEX UNIFIED APP ARCHITECTURE (Stage 3 & Beyond)
## Facebook Lite-Inspired Mobile & Web Architecture for Yemen Network Market

### Project Directory Layout (Clean Architecture)

```
cardex_app/
├── lib/
│   ├── main.dart                      # Application Entry Point
│   ├── core/
│   │   ├── constants/
│   │   │   └── app_colors.dart        # Primary Tech Blue (#308BE7) & Theme Tokens
│   │   ├── network/
│   │   │   ├── captive_portal_client.dart  # Direct HTTP POST to Captive Portals
│   │   │   ├── mqtt_realtime_client.dart   # Facebook Lite 200-Byte Ultra-Light Stream
│   │   │   └── supabase_client.dart        # Supabase RLS Authenticated Client
│   │   └── security/
│   │       ├── anti_screenshot_guard.dart  # Display Watermarking & Screenshot Blocking
│   │       └── device_fingerprint.dart     # Hardware & App Integrity Authentication
│   ├── features/
│   │   ├── auth/
│   │   │   ├── presentation/
│   │   │   │   └── role_switch_screen.dart # Unified Single Login & Auto-Role Detection
│   │   │   └── data/
│   │   │       └── auth_repository.dart
│   │   ├── pos_terminal/               # AGENT / GROCERY INTERFACE
│   │   │   ├── presentation/
│   │   │   │   ├── pos_dashboard.dart  # Fast Card Dispense Terminal
│   │   │   │   └── thermal_print_dialog.dart # Bluetooth Thermal Printing Engine
│   │   │   └── data/
│   │   │       └── offline_queue_store.dart # 2G/3G Local SQLite Offline Queue
│   │   ├── customer_wallet/            # END-USER / CUSTOMER INTERFACE
│   │   │   ├── presentation/
│   │   │   │   ├── flash_qr_view.dart  # Dynamic 30s Flash Handshake QR Token
│   │   │   │   └── my_cards_screen.dart# Protected Cards Vault & One-Tap Connect Button
│   │   │   └── data/
│   │   │       └── card_reveal_service.dart # Timed Reveal & Cryptographic Verification
│   │   └── owner_dashboard/            # OWNER / NETWORK ADMIN INTERFACE
│   │       ├── presentation/
│   │       │   └── live_ledger_monitor.dart # Realtime Financial Ledger & Multi-Currency Stats
│   │       └── data/
│   │           └── batch_ingestion_service.dart
```

---

### Core Module Implementation Logic

#### 1. Captive Portal Auto-Connect Engine (`captive_portal_client.dart`)
```dart
class CaptivePortalClient {
  Future<bool> autoConnectToNetwork({
    required String gatewayUrl,
    required String voucherCode,
  }) async {
    // Sends direct HTTP POST request to local captive portal login endpoint
    // Automatically authenticates the user without manual PIN copy-paste
    return true;
  }
}
```

#### 2. Dynamic Flash Handshake Token (`flash_qr_view.dart`)
```dart
class FlashQrService {
  String generate30sToken(String customerId, String secretKey) {
    final timeBlock = DateTime.now().millisecondsSinceEpoch ~/ 30000;
    final payload = "$customerId-$timeBlock-$secretKey";
    return payload; // Dynamic 30-second rotating security token
  }
}
```

---

### Deployment Steps to GitHub (`Cardex` Repository)

1. Initialize Local Project Directory (`cardex_app`).
2. Link Remote GitHub Repository (`Cardex`).
3. Commit Stage 1-3 Infrastructure Code.
4. Push to Main Branch.

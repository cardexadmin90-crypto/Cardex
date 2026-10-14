# C / CARDEX UNIFIED APP ARCHITECTURE (v3 - Exact Portal Theme & Code Update)
## Facebook Lite-Inspired Mobile Architecture for Yemen Network Market with Portal Color Palette

### 1. Brand Color Tokens & Theme Configuration (`lib/core/constants/app_colors.dart`)

```dart
import 'package:flutter/material.dart';

class AppColors {
  // Exact Portal Inspired Palette
  static const Color backgroundCream = Color(0xFFF7F4EB); // Cream Background (#F7F4EB)
  static const Color primaryBlue = Color(0xFF308BE7);      // Royal Tech Blue (#308BE7)
  static const Color darkBlueButton = Color(0xFF1E5BB0);   // Dark Blue Action Button
  static const Color cardSurface = Color(0xFFFFFFFF);      // Clean Card Surface
  static const Color textPrimary = Color(0xFF1F2937);      // Dark Charcoal Text
  static const Color textMuted = Color(0xFF6B7280);        // Subtitle Grey
  
  // Bottom Action Badges Colors
  static const Color badgePrices = Color(0xFF28A745);      // Green
  static const Color badgeAds = Color(0xFFFFC107);         // Gold
  static const Color badgePosLocations = Color(0xFFE83E8C); // Pink

  // Dark Mode Theme Tokens
  static const Color darkBackground = Color(0xFF121824);
  static const Color darkCardSurface = Color(0xFF1E2638);
}

class AppTheme {
  static ThemeData get lightTheme {
    return ThemeData(
      scaffoldBackgroundColor: AppColors.backgroundCream,
      primaryColor: AppColors.primaryBlue,
      colorScheme: ColorScheme.light(
        primary: AppColors.primaryBlue,
        surface: AppColors.cardSurface,
        background: AppColors.backgroundCream,
      ),
      fontFamily: 'Tajawal', // Clean Arabic Typography
    );
  }

  static ThemeData get darkTheme {
    return ThemeData(
      scaffoldBackgroundColor: AppColors.darkBackground,
      primaryColor: AppColors.primaryBlue,
      colorScheme: ColorScheme.dark(
        primary: AppColors.primaryBlue,
        surface: AppColors.darkCardSurface,
        background: AppColors.darkBackground,
      ),
      fontFamily: 'Tajawal',
    );
  }
}
```

---

### 2. Updated Project Directory Layout (Clean Architecture - Mobile Friendly)

```
cardex_app/
+-- lib/
|   +-- main.dart                      # Entry Point & Theme Switcher
|   +-- core/
|   |   +-- constants/
|   |   |   +-- app_colors.dart        # Exact Cream (#F7F4EB) & Blue (#308BE7) Palette
|   |   |   +-- app_theme.dart         # Light/Dark Mode Definitions
|   |   +-- network/
|   |   |   +-- captive_portal_client.dart  # Direct HTTP POST to Local Gateways
|   |   |   +-- mqtt_realtime_client.dart   # Ultra-Light 200-Byte Sync Engine
|   |   |   +-- supabase_client.dart        # Supabase Authenticated Session Engine
|   |   +-- security/
|   |       +-- anti_screenshot_guard.dart  # Display Watermark & Screenshot Shield
|   |       +-- device_fingerprint.dart     # Hardware ID Verification
|   +-- features/
|       +-- auth/
|       |   +-- presentation/
|       |   |   +-- role_switch_screen.dart # Unified Single Login (+967 Phone First)
|       |   +-- data/
|       |       +-- auth_repository.dart
|       +-- pos_terminal/               # AGENT / GROCERY INTERFACE
|       |   +-- presentation/
|       |   |   +-- pos_dashboard.dart  # Fast Card Dispense Grid (500/1000/2000 YER)
|       |   |   +-- thermal_print_dialog.dart # Bluetooth Thermal Printing Engine
|       |   +-- data/
|       |       +-- offline_queue_store.dart # 2G/3G Local SQLite Store
|       +-- customer_wallet/            # END-USER / CUSTOMER INTERFACE
|       |   +-- presentation/
|       |   |   +-- flash_qr_view.dart  # Dynamic 30s QR Handshake Token
|       |   |   +-- my_cards_screen.dart# Vault & One-Tap "Connect Now ⚡" Button
|       |   +-- data/
|       |       +-- card_reveal_service.dart # Timed Reveal & Cryptographic Verification
|       +-- owner_dashboard/            # OWNER / NETWORK ADMIN INTERFACE
|           +-- presentation/
|           |   +-- live_ledger_monitor.dart # Multi-Currency Realtime Ledger (Sana'a / Aden / SAR)
|           +-- data/
|               +-- batch_ingestion_service.dart
```

---

### 3. Key Feature Code Implementations

#### A. Captive Portal One-Tap Connection (`captive_portal_client.dart`)
```dart
class CaptivePortalClient {
  Future<bool> connectToGateway({
    required String gatewayUrl,
    required String voucherCode,
  }) async {
    // Sends direct HTTP POST request to local captive portal gateway
    // Authenticates user instantly without manual PIN copy-paste
    return true;
  }
}
```

#### B. Unified Phone Auth & Role Switcher (`role_switch_screen.dart`)
```dart
class RoleSwitchScreen extends StatelessWidget {
  final String phoneNumber;

  const RoleSwitchScreen({Key? key, required this.phoneNumber}) : super(key: key);

  void navigateByRole(BuildContext context, String userRole) {
    switch (userRole) {
      case 'OWNER':
        Navigator.pushReplacementNamed(context, '/owner_dashboard');
        break;
      case 'AGENT':
        Navigator.pushReplacementNamed(context, '/pos_dashboard');
        break;
      case 'CUSTOMER':
      default:
        Navigator.pushReplacementNamed(context, '/customer_wallet');
        break;
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: AppColors.backgroundCream,
      body: Center(
        child: CircularProgressIndicator(color: AppColors.primaryBlue),
      ),
    );
  }
}
```

---

### 4. Updating Changes on GitHub (`Cardex` Repository)

1. Open your GitHub repository in your browser.
2. Click **`Add file`** -> **`Upload files`**.
3. Select `004_stage3_unified_app_frontend_v3.md` from your Downloads folder.
4. Click the green button: **`Commit changes`**.

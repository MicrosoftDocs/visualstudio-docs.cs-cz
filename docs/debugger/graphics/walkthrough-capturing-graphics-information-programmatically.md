---
title: Programové zachycení informací grafiky
description: Podívejte se, jak používat Visual Studio Diagnostika grafiky k programovému zachycení informací grafiky z aplikace Direct3D.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5375ac252d097234cf81d1802be1ab681f90bbcd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995006"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu programu
Pomocí Diagnostika grafiky můžete [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programově zachytit grafické informace z aplikace Direct3D.

Programové zachytávání je užitečné ve scénářích, jako jsou:

- Pokud vaše grafická aplikace nepoužívá swapchain k dispozici, začněte zachytit programově, například když se vykresluje na texturu.

- Pokud se vaše aplikace vůbec nevykresluje, můžete zachytávání spustit programově, například když k provádění výpočtů používá DirectCompute.

- Volá `CaptureCurrentFrame` se v případě, že problém s vykreslováním je obtížné odhadnout a zachytit v manuálním testování, ale dá se předpovědět programově pomocí informací o stavu aplikace za běhu.

## <a name="programmatic-capture-in-windows-10"></a><a name="CaptureDX11_2"></a> Programové zachycení ve Windows 10
Tato část návodu ukazuje programové zachycení v aplikacích, které používají rozhraní DirectX 11,2 API ve Windows 10, které používá robustní metodu zachycení.

V této části se dozvíte, jak provádět tyto úlohy:

- Příprava aplikace pro použití programového zachycení

- Získání rozhraní IDXGraphicsAnalysis

- Zachycení informací grafiky

> [!NOTE]
> Předchozí implementace programového zachycení se spoléhaly na Remote Tools for Visual Studio, aby poskytovaly funkci zachycení.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Příprava aplikace pro použití programového zachycení
Pokud chcete ve své aplikaci použít programové zachycení, musí obsahovat potřebné hlavičky. Tato záhlaví jsou součástí sady Windows 10 SDK.

##### <a name="to-include-programmatic-capture-headers"></a>Zahrnutí programových hlaviček zachycení

- Zahrňte tyto hlavičky do zdrojového souboru, kde budete definovat rozhraní IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Nezahrnovat hlavičkový soubor vsgcapture. h, který podporuje Programové zachycení na Windows 8,0 a starší verzi – k provádění programového zachycení v aplikacích pro Windows 10. Tato hlavička není kompatibilní s rozhraním DirectX 11,2. Pokud je tento soubor zahrnutý po zahrnutí hlavičky d3d11_2. h, vyvolá kompilátor upozornění. Pokud je vsgcapture. h zahrnuté před d3d11_2. h, aplikace se nespustí.

    > [!NOTE]
    > Pokud je v počítači nainstalovaná sada DirectX 2010 DirectX SDK a cesta k zahrnutí vašeho projektu obsahuje `%DXSDK_DIR%includex86` , přesuňte ji na konec cesty include. Proveďte stejnou cestu ke knihovně.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis
Předtím, než budete moci zachytit informace grafiky z rozhraní DirectX 11,2, je nutné získat rozhraní ladění DXGI.

> [!IMPORTANT]
> Pokud používáte programové zachycení, musíte pořád spustit aplikaci v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ) nebo v rámci [Nástroje pro zachycení z příkazového řádku](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis

- Použijte následující kód k připojení rozhraní IDXGraphicsAnalysis k ladicímu rozhraní DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Ujistěte se, že jste zkontrolovali `HRESULT` vrácenou funkcí [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) , abyste zajistili, že budete mít platné rozhraní předtím, než ho použijete:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Pokud `DXGIGetDebugInterface1` vrátí hodnotu `E_NOINTERFACE` ( `error: E_NOINTERFACE No such interface supported` ), ujistěte se, že aplikace běží v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ).

### <a name="capturing-graphics-information"></a>Zachycení informací grafiky
Teď, když máte platné `IDXGraphicsAnalysis` rozhraní, můžete `BeginCapture` `EndCapture` k zachycení informací grafiky použít a.

##### <a name="to-capture-graphics-information"></a>Zachycení informací grafiky

- Chcete-li začít zachytávání informací o grafice, použijte `BeginCapture` :

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Zachytávání začíná okamžitě po `BeginCapture` volání; nečeká na zahájení dalšího snímku. Zachytávání se zastaví, když se zobrazí aktuální rámec, nebo když zavoláte `EndCapture` :

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Po volání `EndCapture` uvolněte objekt Graphics.

## <a name="next-steps"></a>Další kroky
Tento návod ukázal, jak programově zachytit informace grafiky. Jako další krok zvažte tuto možnost:

- Naučte se analyzovat informace o zachycených grafikách pomocí nástrojů Diagnostika grafiky. Další informace najdete v tématu [Přehled](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Viz také
- [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)
- [Zaznamenání grafických informací](capturing-graphics-information.md)
- [Nástroj příkazového řádku pro zachytávání](command-line-capture-tool.md)

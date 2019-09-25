---
title: 'Návod: Programové zachycení informací grafiky | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 187328e4ef4d1de0c865120400f84e65385160fc
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252897"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu programu
Pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafiky můžete programově zachytit grafické informace z aplikace Direct3D.

Programové zachytávání je užitečné ve scénářích, jako jsou:

- Pokud vaše grafická aplikace nepoužívá swapchain k dispozici, začněte zachytit programově, například když se vykresluje na texturu.

- Pokud se vaše aplikace vůbec nevykresluje, můžete zachytávání spustit programově, například když k provádění výpočtů používá DirectCompute.

- Volá `CaptureCurrentFrame`se v případě, že problém s vykreslováním je obtížné odhadnout a zachytit v manuálním testování, ale dá se předpovědět programově pomocí informací o stavu aplikace za běhu.

## <a name="CaptureDX11_2"></a>Programové zachycení ve Windows 10
Tato část návodu ukazuje programové zachycení v aplikacích, které používají rozhraní DirectX 11,2 API ve Windows 10, které používá robustní metodu zachycení.

V této části se dozvíte, jak provádět tyto úlohy:

- Příprava aplikace pro použití programového zachycení

- Získání rozhraní IDXGraphicsAnalysis

- Zachycení informací grafiky

> [!NOTE]
> Předchozí implementace programového zachycení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se spoléhaly na Remote Tools for Visual Studio, aby poskytovaly funkci zachycení.

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
    > Nezahrnovat hlavičkový soubor vsgcapture. h, který podporuje Programové zachycení na Windows 8,0 a starší verzi – k provádění programového zachycení v aplikacích pro Windows 10. Tato hlavička není kompatibilní s rozhraním DirectX 11,2. Pokud je tento soubor zahrnut po zahrnutí hlavičky d3d11_2. h, vyvolá kompilátor upozornění. Pokud je vsgcapture. h zahrnutý před d3d11_2. h, aplikace se nespustí.

    > [!NOTE]
    > Pokud je v počítači nainstalovaná sada DirectX 2010 DirectX SDK a cesta k zahrnutí vašeho projektu obsahuje `%DXSDK_DIR%includex86`, přesuňte ji na konec cesty include. Proveďte stejnou cestu ke knihovně.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis
Předtím, než budete moci zachytit informace grafiky z rozhraní DirectX 11,2, je nutné získat rozhraní ladění DXGI.

> [!IMPORTANT]
> Pokud používáte programové zachycení, musíte pořád spustit aplikaci v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) nebo v rámci [Nástroje pro zachycení z příkazového řádku](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis

- Použijte následující kód k připojení rozhraní IDXGraphicsAnalysis k ladicímu rozhraní DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Ujistěte se, že jste `HRESULT` zkontrolovali vrácenou funkcí [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) , abyste zajistili, že budete mít platné rozhraní předtím, než ho použijete:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Pokud `DXGIGetDebugInterface1` vrátí `E_NOINTERFACE` hodnotu(`error: E_NOINTERFACE No such interface supported`), ujistěte se, že aplikace běží v rámci diagnostiky grafiky (ALT [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]+ F5 v).

### <a name="capturing-graphics-information"></a>Zachycení informací grafiky
Teď, když máte platné `IDXGraphicsAnalysis` rozhraní, můžete k zachycení informací grafiky použít `BeginCapture` a `EndCapture` .

##### <a name="to-capture-graphics-information"></a>Zachycení informací grafiky

- Chcete-li začít zachytávání informací `BeginCapture`o grafice, použijte:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Zachytávání začíná okamžitě `BeginCapture` po volání; nečeká na zahájení dalšího snímku. Zachytávání se zastaví, když se zobrazí aktuální rámec, nebo když `EndCapture`zavoláte:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Po volání `EndCapture`uvolněte objekt Graphics.

## <a name="next-steps"></a>Další kroky
Tento návod ukázal, jak programově zachytit informace grafiky. Jako další krok zvažte tuto možnost:

- Naučte se analyzovat informace o zachycených grafikách pomocí nástrojů Diagnostika grafiky. Další informace najdete v tématu [Přehled](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Viz také
- [Návod: Záznam grafických informací](walkthrough-capturing-graphics-information.md)
- [Zaznamenání grafických informací](capturing-graphics-information.md)
- [Nástroj příkazového řádku pro zachytávání](command-line-capture-tool.md)

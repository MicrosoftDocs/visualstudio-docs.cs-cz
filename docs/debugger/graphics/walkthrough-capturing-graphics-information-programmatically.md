---
title: 'Návod: Programové zachycení informací grafiky | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2036588fe04825b0fe1a1aa2db7ae8f7e0b5ad4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734773"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Návod: Zaznamenání grafických informací prostřednictvím kódu
@No__t_0 Diagnostika grafiky můžete použít k programovému zachycení informací grafiky z aplikace Direct3D.

Programové zachytávání je užitečné ve scénářích, jako jsou:

- Pokud vaše grafická aplikace nepoužívá swapchain k dispozici, začněte zachytit programově, například když se vykresluje na texturu.

- Pokud se vaše aplikace vůbec nevykresluje, můžete zachytávání spustit programově, například když k provádění výpočtů používá DirectCompute.

- Volání `CaptureCurrentFrame`when problému s vykreslováním je obtížné odhadnout a zachytit v manuálním testování, ale lze je předpovědět pomocí informací o stavu aplikace v době běhu.

## <a name="CaptureDX11_2"></a>Programové zachycení ve Windows 10
Tato část návodu ukazuje programové zachycení v aplikacích, které používají rozhraní DirectX 11,2 API ve Windows 10, které používá robustní metodu zachycení.

V této části se dozvíte, jak provádět tyto úlohy:

- Příprava aplikace pro použití programového zachycení

- Získání rozhraní IDXGraphicsAnalysis

- Zachycení informací grafiky

> [!NOTE]
> Předchozí implementace programového sběru se spoléhaly na Remote Tools for Visual Studio, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytují funkci zachycení.

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
> Při použití programového zachycení je nutné pořád spustit aplikaci v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) nebo v rámci [Nástroje pro zachycení z příkazového řádku](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Získání rozhraní IDXGraphicsAnalysis

- Použijte následující kód k připojení rozhraní IDXGraphicsAnalysis k ladicímu rozhraní DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Nezapomeňte zkontrolovat `HRESULT` vrácených funkcí [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) , abyste zajistili, že budete mít k dispozici platné rozhraní před jeho použitím:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Pokud `DXGIGetDebugInterface1` vrátí `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), ujistěte se, že je aplikace spuštěná v rámci diagnostiky grafiky (ALT + F5 v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).

### <a name="capturing-graphics-information"></a>Zachycení informací grafiky
Teď, když máte platné `IDXGraphicsAnalysis` rozhraní, můžete k zachycení informací grafiky použít `BeginCapture` a `EndCapture`.

##### <a name="to-capture-graphics-information"></a>Zachycení informací grafiky

- Chcete-li začít zachytávání informací o grafice, použijte `BeginCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Zachytávání začíná ihned při volání `BeginCapture`; nečeká na zahájení dalšího snímku. Zachycení se zastaví, když se zobrazí aktuální rámec, nebo když zavoláte `EndCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Po volání `EndCapture` uvolněte objekt Graphics.

## <a name="next-steps"></a>Další kroky
Tento návod ukázal, jak programově zachytit informace grafiky. Jako další krok zvažte tuto možnost:

- Naučte se analyzovat informace o zachycených grafikách pomocí nástrojů Diagnostika grafiky. Další informace najdete v tématu [Přehled](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Viz také:
- [Návod: Zaznamenání grafických informací](walkthrough-capturing-graphics-information.md)
- [Zaznamenání grafických informací](capturing-graphics-information.md)
- [Nástroj příkazového řádku pro zachytávání](command-line-capture-tool.md)

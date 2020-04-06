---
title: Registrace vyhodnocení výrazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713200"
---
# <a name="register-an-expression-evaluator"></a>Registrace vyhodnocení výrazu
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Vyhodnocení výrazu (EE) se musí zaregistrovat jako továrna třídy s prostředím Windows COM a Visual Studio. EE je nastavena jako DLL tak, aby se vstřikuje do adresního prostoru ladicí modul (DE) nebo Visual Studio adresní prostor, v závislosti na entita, která instance ee.

## <a name="managed-code-expression-evaluator"></a>Vyhodnocení spravovaného výrazu kódu
 Spravovaný kód EE je implementován jako knihovna tříd, což je knihovna DLL, která se registruje v prostředí COM, obvykle spuštěné voláním programu VSIP, *regpkg.exe*. Skutečný proces zápisu klíčů registru pro prostředí COM je zpracován automaticky.

 Metoda hlavní třídy je <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>označena , což znamená, že metoda má být volána při registraci dll u com. Tato metoda registrace, `RegisterClass`často volal , provádí úlohu registrace DLL s Visual Studio. Odpovídající `UnregisterClass` (označené <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), vrátí účinky `RegisterClass` při odinstalaci dll.
Stejné položky registru jsou provedeny jako pro EE napsané v nespravovaném kódu; jediným rozdílem je, že neexistuje žádná `SetEEMetric` pomocná funkce, jako je dělat práci za vás. Následuje příklad procesu registrace a zrušení registrace.

### <a name="example"></a>Příklad
 Následující funkce ukazuje, jak spravovaný kód EE registruje a zruší registraci sám s Visual Studio.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        #region Register and unregister.
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");
        private static string languageName = "MyC";
        private static string eeName = "MyC Expression Evaluator";

        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");

        /// <summary>
        /// Register the expression evaluator.
        /// Set "project properties/configuration properties/build/register for COM interop" to true.
        /// </summary>
         [ComRegisterFunctionAttribute]
        public static void RegisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator";

            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);
            if (rk == null)  return;

            rk = rk.CreateSubKey(guidMycLang.ToString("B"));
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));
            rk.SetValue("CLSID", t.GUID.ToString("B"));
            rk.SetValue("Language", languageName);
            rk.SetValue("Name", eeName);

            rk = rk.CreateSubKey("Engine");
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));
        }
        /// <summary>
        /// Unregister the expression evaluator.
        /// </summary>
         [ComUnregisterFunctionAttribute]
        public static void UnregisterClass(Type t)
        {
            // Get Visual Studio version (set by regpkg.exe)
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");
            string s = @"SOFTWARE\Microsoft\VisualStudio\"
                        + hive
                        + @"\AD7Metrics\ExpressionEvaluator\"
                        + guidMycLang.ToString("B");
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);
            if (key != null)
            {
                key.Close();
                Registry.LocalMachine.DeleteSubKeyTree(s);
            }
        }
    }
}
```

## <a name="unmanaged-code-expression-evaluator"></a>Vyhodnocení nespravovaného výrazu kódu
 EE DLL implementuje `DllRegisterServer` funkci zaregistrovat sám s prostředím COM, stejně jako Visual Studio.

> [!NOTE]
> Ukázkový kód registru kódu MyCEE naleznete v souboru *dllentry.cpp*, který je umístěn v instalaci VSIP pod envsdk\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Proces serveru DLL
 Při registraci EE server DLL:

1. Registruje svou `CLSID` třídu podle běžných konvencí COM.

2. Volá pomocnou `SetEEMetric` funkci zaregistrovat s Visual Studio Metriky EE uvedené v následující tabulce. Funkce `SetEEMetric` a metriky zadané následujícím způsobem jsou součástí knihovny *dbgmetric.lib.* Podrobnosti naleznete [v pomocných sponessss sdsad.](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

    |Metrika|Popis|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`třídy EE|
    |`metricName`|Název EE jako zobrazitelný řetězec|
    |`metricLanguage`|Název jazyka, který je EE určen k vyhodnocení|
    |`metricEngine`|`GUID`ladicích motorů (DE), které pracují s tímto EE|

    > [!NOTE]
    > Identifikuje `metricLanguage``GUID` jazyk podle názvu, ale je `guidLang` `SetEEMetric` argument, který vybere jazyk. Když kompilátor generuje soubor informací o ladění, `guidLang` měl by napsat příslušný, aby DE věděl, které EE použít. DE obvykle požádá zprostředkovatele symbolů `GUID`pro tento jazyk , který je uložen v souboru informací o ladění.

3. Registruje se v sadě Visual Studio vytvořením klíčů\\v části HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, kde *X.Y* je verze sady Visual Studio, u které se chcete zaregistrovat.

### <a name="example"></a>Příklad
 Následující funkce ukazuje, jak nespravovaný kód (C++) EE registruje a zruší registraci sám s Visual Studio.

```cpp
/*---------------------------------------------------------
  Registration
-----------------------------------------------------------*/
#ifndef LREGKEY_VISUALSTUDIOROOT
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"
#endif

static HRESULT RegisterMetric( bool registerIt )
{
    // check where we should register
    const ULONG cchBuffer = _MAX_PATH;
    WCHAR wszRegistrationRoot[cchBuffer];
    DWORD cchFreeBuffer = cchBuffer - 1;
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);
    wcscat(wszRegistrationRoot, L"\\");

    // this is Environment SDK specific
    // we check for  EnvSdk_RegKey environment variable to
    // determine where to register
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;
    DWORD cchEnvVarRead = GetEnvironmentVariableW(
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value
        /* DWORD   */ cchFreeBuffer);// size of buffer
    if (cchEnvVarRead >= cchFreeBuffer)
        return E_UNEXPECTED;
    // If the environment variable does not exist then we must use
    // LREGKEY_VISUALSTUDIOROOT which has the version number.
    if (0 == cchEnvVarRead)
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);

    if (registerIt)
    {
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricCLSID,
                    CLSID_MycEE,
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricName,
                    GetString(IDS_INFO_MYCDESCRIPTION),
                    wszRegistrationRoot );
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricLanguage, L"MyC",
                    wszRegistrationRoot);

        GUID engineGuids[2];
        engineGuids[0] = guidCOMPlusOnlyEng;
        engineGuids[1] = guidCOMPlusNativeEng;
        SetEEMetric(guidMycLang,
                    guidMicrosoftVendor,
                    metricEngine,
                    engineGuids,
                    2,
                    wszRegistrationRoot);
    }
    else
    {
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricCLSID,
                        wszRegistrationRoot);
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricName,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricLanguage,
                        wszRegistrationRoot );
        RemoveEEMetric( guidMycLang,
                        guidMicrosoftVendor,
                        metricEngine,
                        wszRegistrationRoot );
    }

    return S_OK;
}
```

## <a name="see-also"></a>Viz také
- [Zápis vyhodnocení výrazu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Pomocné spoje sady SDK pro ladění](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

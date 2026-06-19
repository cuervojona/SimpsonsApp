Nombre: Jonathan
Apellido: Tola
Legajo: 1079791
Link:
https://github.com/cuervojona/SimpsonsApp

Issues:

1) 
Archivo: EpisodeRemoteMediator.kt
Línea 105
Contiene el path que debe estar configurado en DataModule.kt cómo baseUrl

2) Error contrato EpisodeRepository.kt 
Línea 23 del archivo: EpisodeRepositoryImpl.kt
No sigue el contrato de la interfaz.
Contrato: fun get_episodes(): Flow<PagingData<Episode>>
Error: 
override fun getEpisodes(): Flow<PagingData<Episode>> {
Solución: Cambiar el nombre en la implementación tal cómo indica el contrato.

3) Archivo: AppNavigation.kt y DetailViewModel.kt
Líneas: AppNavigation.kt líneas 26-35 
DetailViewModel.kt líneas 24-28
Problema: la ruta define episodeId, pero el detalle depende de SavedStateHandle y el argumento no se usa de forma consistente
Solución: asegurar que episodeId se pase y se reciba correctamente en el destino.

4) 
Archivos: DataRepository.kt, MainScreenViewModel.kt, MainScreen.kt
Líneas: 
DataRepository.kt líneas 6-12 
MainScreenViewModel.kt líneas 12-17 
MainScreen.kt líneas 40-43
Problema: hay dos tipos de arqutiecturas distintas. Una está sin uso real
Solución: Unificar en MainViewModel y eliminar el código que no se utiliza

5) 
Archivo: MainScreen.kt
Líneas: 78-113
Problema: el selector de episodios está hardcodeado con 1..25(línea 94) y depende solo de los elementos cargados en memoria.
Solución: construir el selector a partir de datos reales y no de un rango fijo.

6) 
Archivo: MainScreen.kt
Líneas: 50-53
Problema: el Composable dispara una actualización del ViewModel (refreshSeasons) según el estado de Paging.
Solución: mover esa lógica al ViewModel.

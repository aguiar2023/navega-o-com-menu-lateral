import React from 'react';
import { View, Text, Button, StyleSheet } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import { createDrawerNavigator } from '@react-navigation/drawer';
import { createMaterialTopTabNavigator } from '@react-navigation/material-top-tabs';

// Estilos
const estilos = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f5f5f5',
  },
  texto: {
    fontSize: 20,
    marginBottom: 20,
  },
});

// Telas para Swipes (3 módulos, cada um com 3 telas)
const SwipeScreen1 = () => (
  <View style={estilos.container}><Text style={estilos.texto}>Tela 1: Bem-vindo ao curso!</Text></View>
);
const SwipeScreen2 = () => (
  <View style={estilos.container}><Text style={estilos.texto}>Tela 2: Como usar o app</Text></View>
);
const SwipeScreen3 = () => (
  <View style={estilos.container}><Text style={estilos.texto}>Tela 3: Dicas iniciais</Text></View>
);

// Configuração do Top Tab Navigator para cada Módulo
const Tab = createMaterialTopTabNavigator();
const ModuloTabs = () => (
  <Tab.Navigator>
    <Tab.Screen name="Tela 1" component={SwipeScreen1} />
    <Tab.Screen name="Tela 2" component={SwipeScreen2} />
    <Tab.Screen name="Tela 3" component={SwipeScreen3} />
  </Tab.Navigator>
);

// Configuração das Stacks (HomeStack)
const Pilha = createStackNavigator();
const HomeStack = () => (
  <Pilha.Navigator>
    <Pilha.Screen name="Módulo 1" component={ModuloTabs} />
    <Pilha.Screen name="Módulo 2" component={ModuloTabs} />
    <Pilha.Screen name="Módulo 3" component={ModuloTabs} />
  </Pilha.Navigator>
);

// Tela simples: Perfil
const PerfilScreen = () => (
  <View style={estilos.container}>
    <Text style={estilos.texto}>👤 Perfil do Usuário</Text>
    <Button title="Editar Perfil" onPress={() => {}} />
  </View>
);

// Tela simples: Configurações
const ConfiguracoesScreen = () => (
  <View style={estilos.container}>
    <Text style={estilos.texto}>⚙️ Configurações</Text>
    <Button title="Tema Escuro/Claro" onPress={() => {}} />
    <Button title="Notificações" onPress={() => {}} />
    <Button title="Idioma" onPress={() => {}} />
  </View>
);

// Drawer Navigation
const Gaveta = createDrawerNavigator();
const NavegacaoGaveta = () => (
  <Gaveta.Navigator initialRouteName="🏠 Home">
    <Gaveta.Screen name="🏠 Home" component={HomeStack} />
    <Gaveta.Screen name="👤 Perfil" component={PerfilScreen} />
    <Gaveta.Screen name="⚙️ Configurações" component={ConfiguracoesScreen} />
  </Gaveta.Navigator>
);

// Componente Principal
export default function App() {
  return (
    <NavigationContainer>
      <NavegacaoGaveta />
    </NavigationContainer>
  );
}

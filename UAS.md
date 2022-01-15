# UAS-Mobile-Device
import * as React from 'react';
import { Button, Text, View } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import Ionicons from 'react-native-vector-icons/Ionicons';


function HomeScreen({navigation}) {
  return (
    <View style={{ flex: 1, justifyContent: 'space-between', alignItems: 'center' }}>
      <Text style={{fontSize:'20px', fontWeight:'bold'}}>Welcome!</Text>
      <Text style={{fontSize:'16px', backgroundColor:'pink', fontWeight:'bold'}}> Hope you will have a nice day!</Text>
      <Button
        title="Go to My Page"
        onPress={( ) => navigation.navigate('MyPage')}
      />
    </View>
  );
}

function MyPage() {
  return (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text style ={{backgroundColor:"pink", fontWeight:'bold'}}>
      Name : Dhivi Rizki Ramadhani 
      </Text>
      <Text style ={{backgroundColor:"pink", fontWeight:'bold'}}>
      Date of Birth : 17th August 2001 
      </Text>
      <Text style ={{backgroundColor:"pink", fontWeight:'bold'}}>
      Age : 20 years old
      </Text>
    </View>
  );
}


const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator
      screenOptions={({ route }) => ({
          tabBarIcon: ({ focused, color, size }) => {
            let iconName;

            if (route.name === 'Home') {
              iconName = focused
                ? 'md-home'
                : 'md-home';
            } else if (route.name === 'MyPage') {
              iconName = focused ? 'md-heart' : 'md-heart';
            }
        
      
            return <Ionicons name={iconName} size={size} color={color} />;
          },
          tabBarActiveTintColor: 'blue',
          tabBarInactiveTintColor: 'red',
        })}
      >
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="MyPage" component={MyPage} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}

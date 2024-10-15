import React, { useState } from "react";
import {
  StyleSheet,
  Text,
  View,
  ScrollView,
  TextInput,
  Button,
  Picker,
  FlatList,
  Image,
} from "react-native";

export default function App() {
  const [language, setLanguage] = useState("tamil");
  const [shows, setShows] = useState([
    { id: "1", name: "Show 1" },
    { id: "2", name: "Show 2" },
    { id: "3", name: "Show 3" },
    { id: "4", name: "Show 4" },
    { id: "5", name: "Show 5" },
    { id: "6", name: "Show 6" },
    { id: "7", name: "Show 7" },
    { id: "8", name: "Show 8" },
    { id: "9", name: "Show 9" },
    { id: "10", name: "Show 10" },
  ]);

  return (
    <ScrollView style={styles.container}>
      {" "}
      <View style={styles.promotionalPanel}>
        <ScrollView horizontal>
          <Text style={styles.promotionalText}>Promotional Content</Text>
        </ScrollView>
        <Image
          source={{
            uri: "https://play-lh.googleusercontent.com/b1b7zLYikzDtCHu2b0c7SnejRhy7Ycjjjd5ZCouYPL3azqpNzp6xzGY_0f1-VR_qYqo=w240-h480-rw",
          }}
          style={styles.logo}
        />
      </View>
      <View style={styles.languageSelector}>
        <Text style={styles.sectionTitle}>Language</Text>
        <Picker
          selectedValue={language}
          style={styles.picker}
          onValueChange={(itemValue) => setLanguage(itemValue)}
        >
          <Picker.Item label="Tamil" value="tamil" />
          <Picker.Item label="Telugu" value="telugu" />
          <Picker.Item label="Malayalam" value="malayalam" />
          <Picker.Item label="Hindi" value="hindi" />
        </Picker>
      </View>
      <View style={styles.languageSelector}>
        <Text style={styles.sectionTitle}>Shows</Text>
        <Picker
          selectedValue={language}
          style={styles.picker}
          onValueChange={(itemValue) => setLanguage(itemValue)}
        >
          <Picker.Item label="show" value=" " />
        </Picker>
      </View>
      <View style={styles.showSection}>
        <Text style={styles.sectionTitle}>Trending Shows</Text>
        <FlatList
          horizontal
          data={shows}
          renderItem={({ item }) => (
            <View style={styles.card}>
              <Text style={styles.cardText}>{item.name}</Text>
              <Text style={styles.cardNumber}>{item.id}</Text>
            </View>
          )}
          keyExtractor={(item) => item.id}
        />
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "yellow",
    padding: 20,
  },
  promotionalPanel: {
    height: 150,
    backgroundColor: "white",
    marginBottom: 20,
    flexDirection: "row",
    justifyContent: "space-between",
    alignItems: "center",
    paddingHorizontal: 10,
  },
  promotionalText: {
    fontSize: 20,
    padding: 10,
  },
  logo: {
    width: 50,
    height: 50,
  },
  languageSelector: {
    marginBottom: 20,
  },
  sectionTitle: {
    fontSize: 18,
    marginBottom: 10,
  },
  picker: {
    height: 30,
    width: 300,
  },
  showSection: {
    flex: 1,
  },
  card: {
    width: 150,
    height: 200,
    backgroundColor: "white",
    marginRight: 10,
    justifyContent: "center",
    alignItems: "center",
    position: "relative",
    borderRadius: 10,
    borderColor: "black",
    borderWidth: 1,
  },
  cardText: {
    fontSize: 16,
  },
  cardNumber: {
    position: "absolute",
    bottom: 5,
    left: 5,
    fontSize: 12,
    color: "gray",
  },
});

